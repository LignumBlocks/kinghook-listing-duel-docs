\# KingHook (Listing Duel) — TECH\_SPEC (Especificación estructural sin código)  
\> Autoridad: este documento vive en \`/docs\` (SoT \= GitHub).
\> Objetivo: evitar drift técnico. Sin código. Sin features fuera de V1.

\#\# Índice  
1\. Alcance técnico V1 (qué se construye / qué no)
2\. Módulos del sistema (caja negra) con inputs/outputs (en humano)
3\. Máquina de estados del usuario (simple)
4\. Datos mínimos por propiedad \+ manejo de data faltante
5\. Fuentes permitidas (categorías) y consumo sin scraping
6\. Contratos de objetos (definiciones)
7\. Scoring V1 (victoria \+ confianza \+ explicación)
8\. Share unit (qué contiene) \+ formatos \+ reglas de claridad
9\. Captura (WhatsApp/email): lead, consentimiento, minimización de PII
10\. Eventos de analytics (por etapa)
11\. Disclaimers y reglas de compliance (lo que NO se afirma)
12\. Mapa de slices sugeridos (S1–S8) \+ gates demo funcional
13\. Reglas anti-drift dentro del build (cambios controlados)
14\. Referencias internas (docs del repo)

\---

\#\# 1\) Alcance técnico V1  
\*\*DECIDIDO (por contexto):\*\*  
\- V1 no depende de scraping de Zillow/Redfin.  
\- V1 es solo buyers.  
\- Lead ≠ llamada: opt-in solo por continuidad (guardar/compartir/shortlist).  
\- Spanish-first.  
\- Miami-Dade y Broward comparten UX; cambian módulos locales.  
\- Núcleo WOW (V1): taxes reset \+ benchmark insurance \+ flood context \+ (condos) señales compliance/financing friction/recert.  
\- Disclaimers: números \= estimaciones/rangos \+ supuestos; sin prometer cash-only/financeable sin evidencia.

\*\*NO se construye en V1 (técnicamente prohibido):\*\*  
\- Extracción automática de datos desde páginas de Zillow/Redfin (scraping).  
\- Verificación bancaria real o underwriting completo.  
\- Promesas “exactas” sin fuentes públicas y sin supuestos.  
\- Sistemas complejos de campañas/CRM (eso vendrá después y se decide en slices futuros).

\---

\#\# 2\) Módulos del sistema (caja negra) con inputs/outputs (en humano)  
\> Nota: “enrichment” aquí significa \*\*usar fuentes permitidas\*\* y/o pedir datos mínimos al usuario cuando falte.

\#\#\# 2.1 Input Capture (captura de entrada)  
\- Input: dos referencias de propiedad (ABIERTO: links / direcciones / mixto).  
\- Output: dos “PropertyCandidate” con lo que se tenga disponible \+ marcas de “faltante”.

\#\#\# 2.2 Normalization (normalización)  
\- Input: PropertyCandidate A y B (parciales).  
\- Output: ambos en formato comparable (mismas etiquetas, mismas unidades, mismos campos).

\#\#\# 2.3 Enrichment (enriquecimiento permitido)  
\- Input: PropertyCandidate con campos faltantes \+ contexto local (condado).  
\- Output: PropertyCandidate con:  
  \- campos completados cuando sea posible con fuentes permitidas,  
  \- o marcados como “no disponible” cuando no sea posible.

\#\#\# 2.4 Scoring (motor del duelo)  
\- Input: dos PropertyCandidate normalizados \+ reglas V1.  
\- Output: DuelResult con:  
  \- ganador,  
  \- score/resumen,  
  \- nivel de confianza,  
  \- trampa principal,  
  \- lista corta de razones (máx. 5).

\#\#\# 2.5 Report Generator (generador de resultado)  
\- Input: DuelResult \+ disclaimers \+ supuestos \+ “faltantes”.  
\- Output: ReportArtifact (resultado visible \+ share unit).

\#\#\# 2.6 Opt-in / Identity (identidad/opt-in)  
\- Input: intención de continuidad (guardar/compartir/shortlist) \+ canal (WhatsApp/email).  
\- Output: LeadRecord (mínimo PII, consentimiento registrado).

\#\#\# 2.7 Shortlist Storage (shortlist)  
\- Input: LeadRecord (o sesión) \+ DuelResult/ReportArtifact.  
\- Output: Shortlist actualizada (lista corta de comparaciones).

\#\#\# 2.8 Readiness Gate (filtro mínimo)  
\- Input: LeadRecord \+ respuestas a 3–5 preguntas.  
\- Output: ReadinessResult (A/B/C) \+ elegibilidad para handoff humano.

\#\#\# 2.9 Handoff Conversion (conversión / siguiente paso humano)  
\- Input: ReadinessResult \+ señal explícita del usuario (“quiero siguiente paso”).  
\- Output: HandoffRequest (registro de solicitud) o ruta alternativa (si no califica).

\---

\#\# 3\) Estados del usuario (máquina de estados simple)  
Estados (orden típico):  
1\) \*\*Anonymous\*\* (sin PII)  
2\) \*\*DuelStarted\*\*  
3\) \*\*ResultViewed\*\*  
4\) \*\*ContinuityIntent\*\* (quiere guardar/compartir/shortlist)  
5\) \*\*OptedIn\*\* (WhatsApp/email)  
6\) \*\*ShortlistActive\*\*  
7\) \*\*ReadinessStarted\*\*  
8\) \*\*ReadinessCompleted\*\*  
9\) \*\*HandoffEligible\*\* (solo si califica)  
10\) \*\*HandoffRequested\*\* (usuario lo pide)  
11\) \*\*Closed/Exit\*\* (sale o termina sesión)

Reglas:  
\- No se puede forzar Opt-in antes de ResultViewed (valor primero).  
\- No se puede llegar a HandoffEligible sin ReadinessCompleted.  
\- HandoffRequested requiere elegibilidad (evita calls basura).

\---

\#\# 4\) Datos mínimos requeridos por propiedad \+ data faltante  
\#\#\# 4.1 Mínimos para correr el duelo (V1)  
\*\*PropertyCandidate debe intentar tener:\*\*  
\- Identificador básico: dirección aproximada o al menos ciudad \+ ZIP (ABIERTO si será obligatorio).  
\- Tipo de propiedad: casa / condo / townhome (al menos “casa vs condo”).  
\- Precio listado (si el usuario no lo provee, se marca faltante).  
\- HOA mensual (si aplica; si no se sabe, “no disponible”).  
\- Condado (Miami-Dade o Broward) para módulos locales.  
\- Señal flood (contexto): ABIERTO según fuente pública disponible.  
\- Contexto de impuestos: ABIERTO (reset escenario depende de fuente y datos disponibles).  
\- Contexto de seguro: ABIERTO (benchmark depende de fuente pública elegida).

\#\#\# 4.2 Regla obligatoria: manejo de “data faltante”  
\- Si falta un campo clave:  
  \- Opción 1 (preferida): mostrar “no disponible” y bajar la confianza.  
  \- Opción 2 (solo si es mínimo y rápido): pedirle al usuario 1 dato puntual.  
\- Prohibido:  
  \- inventar números,  
  \- presentar estimaciones como “hechos”.

\---

\#\# 5\) Fuentes permitidas (categorías) y consumo sin scraping  
\*\*DECIDIDO:\*\* no scraping de Zillow/Redfin.

\#\#\# Categorías permitidas (V1)  
1\) \*\*Datos aportados por el usuario\*\*  
   \- Lo que el usuario pega/ingresa voluntariamente (precio, HOA, dirección, etc.).  
   \- Regla: si el usuario lo aporta, se etiqueta como “provisto por el usuario”.

2\) \*\*Fuentes públicas oficiales (gobierno/condado/estado)\*\*  
   \- Registros/estimadores públicos de impuestos y propiedad (si accesibles sin scraping prohibido).  
   \- Mapas/servicios públicos para contexto flood (si accesibles).  
   \- Regla: si no hay acceso claro/estable, se marca ABIERTO y se usa fallback.

3\) \*\*Fuentes públicas institucionales (lookup verificable)\*\*  
   \- Lookups públicos que permitan verificar señales (p. ej., listas/consultas oficiales aplicables a condos).  
   \- Regla: si no hay verificación directa por esa propiedad, no se afirma.

4\) \*\*Benchmarks públicos agregados\*\*  
   \- Promedios/benchmarks por condado/área para seguro u otros costos, cuando exista fuente pública clara.  
   \- ABIERTO: seleccionar fuente exacta en un slice y registrarlo en DECISION\_LOG.

\#\#\# Consumo “sin scraping”  
\- “Consumir” significa:  
  \- usar APIs/descargas oficiales si existen,  
  \- usar datasets públicos,  
  \- o usar inputs del usuario.  
\- Si la única forma es leer una página privada/portal no permitido → \*\*no se usa\*\* (y se marca faltante).

\---

\#\# 6\) “Contrato” de objetos (definiciones)  
\> Estas definiciones son estructurales; si cambian, se registra en \`DECISION\_LOG.md\`.

\#\### 6.1 PropertyCandidate (contract)

> **Regla estructural**: ambos candidatos de un duelo DEBEN tener la MISMA estructura (mismas keys).
> Campos no disponibles = `null` + key en `missing_fields`.
> Campos estimados = valor + `confidence="low"` (por campo).

| Campo | Tipo | Obligatorio | Default si falta |
|---|---|---:|---|
| `raw_input` | string | sí | `""` |
| `input_kind` | `"url" \| "address_or_text"` | sí | inferido |
| `source_url` | string \| null | sí | `null` |
| `address_text` | string \| null | sí | `null` |
| `city` | string \| null | sí | `null` |
| `state` | string \| null | sí | `null` |
| `zip` | string \| null | sí | `null` |
| `missing_fields` | string[] | sí | `[]` |
| `confidence` | `{ city: "low"\|"unknown", state: "low"\|"unknown", zip: "unknown" }` | sí | ver tipo |

Reglas (Slice 2):

- URL (http/https) => `input_kind="url"` y `source_url` seteado.
- ZIP: patrón de 5 dígitos => `zip` seteado.
- City/State: best-effort desde texto => setear valor y `confidence.city/state="low"`.
- Sin scraping, sin APIs, sin scoring.

\#\#\# 6.2 DuelResult  
\- winner: { A | B | tie | cannot\_determine }  
\- confidence: { alta | media | baja } \+ razón breve  
\- primary\_trap: 1 trampa dominante (texto corto)  
\- reasons: lista (máx 5\) de razones entendibles  
\- assumptions: lista corta de supuestos usados  
\- missing\_data: lista corta de faltantes críticos  
\- disclaimers: referencia a reglas de disclaimers

\#\#\# 6.3 ReportArtifact  
\- duel\_result: DuelResult  
\- share\_unit: objeto listo para compartir (ver sección 8\)  
\- render\_notes: qué mostrar primero y qué es opcional (sin jerga)

\#\#\# 6.4 LeadRecord  
\- lead\_id  
\- channel: { whatsapp | email | ambos } (ABIERTO)  
\- contact\_value: valor (tel/email) minimizado y protegido  
\- consent: { timestamp, purpose: “continuidad”, terms\_version }  
\- created\_at  
\- metadata: { county\_preference?, language\_pref?, source\_campaign? } (mínimo)

\---

\#\# 7\) Scoring V1 (victoria \+ confianza \+ explicación)  
\> Sin fórmulas exactas si no están decididas. Sí estructura.

\#\#\# 7.1 Criterio principal de victoria (V1)  
\- \*\*ABIERTO (con restricción):\*\* debe ser consistente con “anti-sorpresas” y entendible rápido.  
\- Propuesta mínima (compatible con V1):
  \- Ganador \= menor “costo total estimado” \+ menor “riesgo de sorpresa” (sin fingir precisión).

\#\#\# 7.2 Criterios secundarios (V1)  
\- Taxes reset (escenario) como factor de riesgo/costo.  
\- Benchmark insurance como factor de riesgo/costo.  
\- Flood context como señal de riesgo.  
\- Condos: señales de compliance/financing friction/recert como riesgo (sin afirmar financeable/cash-only).

\#\#\# 7.3 Confianza (obligatorio)  
\- Alta: pocos faltantes críticos \+ fuentes claras o datos provistos por usuario completos.  
\- Media: algunos faltantes, pero el veredicto se mantiene razonable.  
\- Baja: faltan datos críticos; el sistema puede no determinar ganador o dar ganador “con reservas”.

\#\#\# 7.4 Explicación (máx 5 bullets)  
Siempre debe incluir:  
\- Por qué gana (1–2 razones),  
\- Trampa principal (1),  
\- Qué falta (1),  
\- Supuesto clave (1).

\---

\#\# 8\) Share unit (qué contiene) \+ formatos \+ reglas de claridad  
\*\*Qué contiene (siempre):\*\*  
\- Ganador (A/B) o “no determinable”.  
\- Trampa principal (1 línea).  
\- 1 diferencia clave (delta en rango o señal principal), sin falsa exactitud.  
\- Confianza (alta/media/baja).  
\- Nota corta de supuestos/faltantes (1 línea).  
\- Disclaimers resumidos.

\*\*Formatos posibles (V1)\*\*  
\- ABIERTO:
  \- texto corto \+ link,
  \- card/imagen,
  \- link con vista resumida.
\- Regla: el formato elegido no puede requerir datos no permitidos ni agregar fricción.

\*\*Reglas de claridad\*\*  
\- Entendible sin contexto en 10 segundos.  
\- No usar jerga; si aparece “HOA/flood”, acompañar con palabra simple (“cuota”, “inundación”).  
\- Nunca afirmar “aprobado/no aprobado por el banco”.

\---

\#\# 9\) Captura (WhatsApp/email): consentimiento y minimización de PII  
\*\*DECIDIDO:\*\* opt-in solo por continuidad (guardar/compartir/shortlist), no por llamada.

\*\*Principios:\*\*  
\- Pedir lo mínimo (1 canal).  
\- Explicar propósito: continuidad del resultado/shortlist.  
\- Registrar consentimiento (timestamp \+ propósito \+ versión).

\*\*PII minimizada:\*\*  
\- No pedir ingresos, SSN, documentos, ni datos sensibles en V1.  
\- Readiness gate (3–5 preguntas) debe evitar números exactos si no están decididos; prioriza bandas/selecciones simples (ABIERTO en PROJECT\_SPEC, se valida).

\---

\#\# 10\) Eventos de analytics (lista)  
\> Eventos deben mapearse a métricas del \`PROJECT\_SPEC.md\`.

Etapa duelo:  
\- duel\_started  
\- duel\_input\_provided  
\- duel\_completed  
\- result\_viewed

Continuidad:  
\- save\_clicked  
\- share\_clicked  
\- shortlist\_created  
\- shortlist\_item\_added

Opt-in:  
\- optin\_started  
\- optin\_completed

Readiness:  
\- readiness\_started  
\- readiness\_completed  
\- readiness\_result\_assigned (A/B/C)

Conversión:  
\- handoff\_eligible  
\- handoff\_requested

Calidad / confianza:  
\- missing\_data\_detected  
\- confidence\_low\_shown  
\- cannot\_determine\_shown

\---

\#\# 11\) Disclaimers y reglas de compliance (qué NO se afirma)  
\*\*Siempre:\*\*  
\- Números \= estimaciones/rangos \+ supuestos.  
\- Si falta data → se muestra y baja confianza.

\*\*Prohibido afirmar:\*\*  
\- “cash-only” sin evidencia verificable.  
\- “financiable” o “te lo aprueban” sin evidencia verificable.  
\- “te va a costar exactamente X” (exactitud falsa).  
\- “esto es asesoría financiera/legal/tributaria”.

\*\*Condos (regla crítica):\*\*  
\- Se puede hablar de “señales de fricción” (riesgo), no de determinaciones definitivas, salvo evidencia pública directa.

\---

\#\# 12\) Slices sugeridos (S1–S8) como mapa (sin ejecutar)  
\> Regla: WIP=1, se ejecuta uno a la vez. Cada slice cierra con “demo funcional (aunque feo)”.

\- \*\*S1 — Entrada Duelo mínima\*\*  
  \- Sale: captura de 2 propiedades (formato ABIERTO elegido) \+ estructura PropertyCandidate.  
  \- Gate: se puede iniciar un duelo y guardar input.

\- \*\*S2 — Normalización \+ data faltante\*\*  
  \- Sale: normalización y regla “faltante → baja confianza”.  
  \- Gate: el sistema muestra faltantes sin romper el flujo.

\- \*\*S3 — Enrichment permitido (mínimo)\*\*  
  \- Sale: integración de al menos 1 categoría de fuente permitida o fallback.  
  \- Gate: evidencia de consumo sin scraping y trazabilidad source\_tag.

\- \*\*S4 — Scoring V1\*\*  
  \- Sale: DuelResult con ganador \+ confianza \+ trampa \+ 3 razones.  
  \- Gate: resultado consistente con faltantes y disclaimers.

\- \*\*S5 — ReportArtifact \+ Share unit\*\*  
  \- Sale: resultado compartible (1 formato elegido).  
  \- Gate: compartible en 10 segundos, sin falsa exactitud.

\- \*\*S6 — Opt-in por continuidad\*\*  
  \- Sale: LeadRecord \+ consentimiento \+ guardar/compartir/shortlist desbloqueado.  
  \- Gate: opt-in ocurre después del resultado.

\- \*\*S7 — Shortlist\*\*  
  \- Sale: shortlist funcional ligada a identidad (lead o sesión).  
  \- Gate: el usuario puede guardar 2–3 duelos y volver.

\- \*\*S8 — Readiness gate \+ handoff\*\*  
  \- Sale: A/B/C \+ handoff eligible/requested.  
  \- Gate: un “C” no llega a handoff; un “A” sí, sin llamadas basura.

\---

\#\# 13\) Reglas anti-drift dentro del build (obligatorias)  
\- No refactors fuera del slice activo.  
\- No cambiar contratos (PropertyCandidate/DuelResult/etc.) sin entrada en \`DECISION\_LOG.md\`.  
\- No agregar campos “por si acaso”; si se propone, va a \`PARKING\_LOT.md\`.  
\- Si algo contradice \`PROJECT\_SPEC.md\` o \`SYSTEM\_MAP.md\`, se detiene y se corrige en docs primero.  
\- La prioridad no cambia hasta cerrar slice (ver \`WORKFLOW\_RULES.md\` y \`CURRENT\_SLICE.md\`).

\---

\#\# 14\) Referencias internas (docs del repo)  
\- \`PROJECT\_SPEC.md\` — contrato maestro (este doc)  
\- \`TECH\_SPEC.md\` — especificación estructural (este doc)  
\- \`PROJECT\_CHARTER.md\` — resumen ejecutivo y límites  
\- \`SYSTEM\_MAP.md\` — mapa de flujo y regla de confianza  
\- \`WORKFLOW\_RULES.md\` — reglas anti-drift y autoridad /docs  
\- \`DECISION\_LOG.md\` — decisiones y condiciones de reapertura  
\- \`CURRENT\_SLICE.md\` — slice activo y gate de cierre  
\- \`PARKING\_LOT.md\` — variaciones pospuestas
