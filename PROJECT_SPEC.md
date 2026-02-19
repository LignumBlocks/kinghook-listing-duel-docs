\# KingHook (Listing Duel) — PROJECT\_SPEC (Contrato maestro)  
\> Autoridad: este documento vive en \`/docs\` (SoT \= GitHub).    
\> Si hay contradicción entre chats y \`/docs\`, gana \`/docs\` (ver \`WORKFLOW\_RULES.md\`).

\#\# Índice  
1\. Qué es KingHook y por qué existe    
2\. Usuario objetivo y contexto Miami/Broward (Spanish-first)    
3\. Principios del producto (V1)    
4\. Flujo end-to-end (de social a conversión)    
5\. Qué incluye V1 / Qué NO incluye V1 (prohibidos)    
6\. Momentos WOW (V1) y por qué son creíbles sin sobreprometer    
7\. Modelo de valor: por qué alguien deja WhatsApp/email (continuidad)    
8\. Segmentación por intención y progresión (frío/tibio/caliente)    
9\. Métricas 30 días y eventos que las alimentan    
10\. Riesgos de confianza y defensas (disclaimers \+ data faltante)    
11\. Supuestos ABIERTO \+ cómo validarlos sin construir todo    
12\. Referencias internas (docs del repo)

\---

\#\# 1\) Qué es KingHook \+ por qué existe  
\*\*Qué es (1 párrafo):\*\*    
KingHook es una herramienta para compradores (solo buyers) hispanohablantes en Miami-Dade y Broward que compara dos propiedades (A vs B) y entrega un veredicto claro de cuál conviene más, junto con la “trampa principal” que puede hacer que la otra termine saliendo más cara (siempre con estimaciones/rangos, supuestos y señalando cuando falta información).

\*\*Por qué existe (dolor real del buyer):\*\*    
El comprador real no falla por “falta de listings”. Falla por \*\*sorpresas\*\*: cree que una propiedad “se ve bien” y decide por fotos/precio/ubicación, pero después se rompe el plan por costos que no tenía en mente (impuestos, seguros, flood, HOA/assessments en condos, fricción de financiamiento). KingHook existe para \*\*reducir sorpresas\*\* y acelerar decisiones razonables en menos de 60 segundos, sin obligar al usuario a revelar datos personales desde el inicio.

\---

\#\# 2\) Usuario objetivo, contexto Miami/Broward, por qué Spanish-first  
\*\*Usuario objetivo (V1):\*\*  
\- Buyer hispanohablante, móvil.  
\- First-time buyer y move-up (no inversionistas como foco).  
\- Está en el “modo comparar” (viendo casas/condos en el teléfono).  
\- Su contexto emocional: quiere elegir rápido, tiene miedo a equivocarse y odia perder tiempo en pasos largos.

\*\*Contexto Miami-Dade vs Broward (DECIDIDO):\*\*  
\- \*\*DECIDIDO:\*\* UX igual (mismo flujo y pantallas).  
\- \*\*DECIDIDO:\*\* Cambian “módulos locales” (p. ej., benchmarks por condado, reglas/avisos locales, contexto flood por zona).    
\- \*\*ABIERTO:\*\* Qué tan granular será lo “local” en V1 (condado vs ZIP vs algo más fino). Consecuencia: más granular \= más precisión, pero más riesgo de data faltante y más complejidad.

\*\*Spanish-first (DECIDIDO):\*\*  
\- Español como base.    
\- \*\*ABIERTO:\*\* Toggle a inglés en V1. Consecuencia: agregar toggle temprano puede distraer; si se hace, que no agregue fricción ni cambie el flujo.

\---

\#\# 3\) Principios del producto (V1)  
1\) \*\*Anti-sorpresas:\*\* el objetivo es detectar y explicar el costo/riesgo dominante, no “ganar por números bonitos”.    
2\) \*\*Claridad \< 60 segundos:\*\* resultado entendible rápido; si hay detalle, es opcional.    
3\) \*\*Primero valor, después datos personales:\*\* el usuario puede obtener un resultado sin entregar teléfono.    
4\) \*\*Continuidad \= opt-in:\*\* lead ≠ llamada. El opt-in se justifica por guardar/compartir/shortlist.    
5\) \*\*Honestidad operativa:\*\* si falta data, se dice; baja la confianza; no se inventa precisión.    
6\) \*\*No prometer lo que no se puede probar:\*\* prohibido afirmar “cash-only/financeable” sin evidencia verificable.

\---

\#\# 4\) Flujo end-to-end (social → landing → duelo → … → conversión)  
\> Este flujo debe permanecer consistente con \`SYSTEM\_MAP.md\`. Si cambia, se registra en \`DECISION\_LOG.md\`.

\#\#\# Etapa A — Descubrimiento (Social/Ads/SEO)  
\- El usuario llega con mentalidad: “estoy comparando opciones” (no: “quiero calificarme”).  
\- La promesa efectiva es inmediata: comparar 2 propiedades y recibir un veredicto.

\#\#\# Etapa B — Landing (entrada sin fricción)  
\- Acción primaria: el usuario introduce \*\*dos propiedades\*\* para comparar.  
\- \*\*DECIDIDO:\*\* V1 no depende de scraping de Zillow/Redfin → si el input es un link, debe funcionar sin leer esas páginas automáticamente.    
\- \*\*ABIERTO:\*\* Formato exacto de input en V1 (2 links, 2 direcciones, o un mix). Consecuencia:    
  \- links \= más cómodo, pero no se puede depender de extraer datos de esos sitios;    
  \- direcciones \= más limpias para fuentes públicas, pero sube fricción.

\#\#\# Etapa C — Duelo (ejecución del motor)  
\- Se recopila/organiza lo mínimo posible con fuentes permitidas y/o datos que el usuario aporta.  
\- Si falta data clave, el sistema:  
  \- o marca “no disponible” y baja confianza,    
  \- o pide un dato mínimo (sin convertirlo en formulario largo).

\#\#\# Etapa D — Resultado (valor inmediato)  
\- Entrega 3 cosas (siempre):  
  1\) veredicto (ganador),    
  2\) trampa principal (lo que más puede salir caro después),    
  3\) transparencia: supuestos \+ qué falta \+ nivel de confianza.

\#\#\# Etapa E — Guardar/Compartir (continuidad)  
\- El usuario naturalmente quiere:  
  \- guardar para revisar luego,    
  \- compartir con pareja/familia.    
\- Aquí es donde el opt-in tiene sentido (ver sección 7).

\#\#\# Etapa F — Shortlist (lista corta)  
\- El usuario acumula comparaciones importantes.  
\- Shortlist reduce el caos mental: “estas 3 finalistas”.

\#\#\# Etapa G — Readiness gate (filtro mínimo)  
\- Aparece cuando el usuario muestra intención real (ej. guarda, comparte, crea shortlist).  
\- Objetivo: evitar llamadas con “C”.

\#\#\# Etapa H — Conversión (siguiente paso humano solo si califica)  
\- Conversión no es “llamada porque sí”.  
\- Conversión sucede cuando:  
  \- el usuario quiere ejecutar (avanzar a ver/ofertar) \*\*y\*\*  
  \- el readiness no lo marca como “no listo”.

\---

\#\# 5\) Qué incluye V1 / Qué NO incluye V1 (prohibidos)  
\*\*Incluye V1 (DECIDIDO por contexto):\*\*  
\- Duelo A vs B (entrada → resultado).  
\- Resultado con estimaciones/rangos \+ supuestos \+ data faltante \= baja confianza.  
\- Guardar/compartir/shortlist como razón de opt-in.  
\- Readiness gate mínimo para evitar llamadas de baja calidad.  
\- Solo buyers.

\*\*NO incluye V1 (prohibidos explícitos):\*\*  
\- Scraping de Zillow/Redfin (DECIDIDO).  
\- Sellers (DECIDIDO).  
\- Prometer exactitud o resultados “garantizados”.  
\- Afirmaciones fuertes sin evidencia (“cash-only”, “aprobado por el banco”, “financiable seguro”).  
\- “Pre-approval” real, underwriting completo, DTI exacto, verificación de documentos.  
\- CRM completo, automatizaciones complejas, multi-canal masivo desde día 1\.  
\- Cualquier “feature sorpresa” no parte del flujo V1 (va a \`PARKING\_LOT.md\`).

\---

\#\# 6\) “Momentos WOW” (V1) y por qué son creíbles  
\*\*DECIDIDO: Núcleo WOW en V1\*\*  
\- Taxes reset (contexto de que los impuestos pueden cambiar tras compra).    
\- Benchmark insurance (comparación con referencia local razonable).    
\- Flood context (señal de contexto flood; sin inventar tasas).    
\- Condos: señales de compliance/financing friction/recertificación (sin afirmar financeable/cash-only sin evidencia).

\*\*Por qué son creíbles sin sobreprometer:\*\*  
\- No se presentan como “verdad absoluta”, sino como:  
  \- “escenarios”,    
  \- “rangos”,    
  \- “señales”,    
  \- “alertas de riesgo”.    
\- Siempre acompañados de supuestos y “qué falta”.

\*\*ABIERTO (control de credibilidad):\*\*  
\- Qué fuentes públicas exactas se usarán para cada WOW (debe definirse en \`TECH\_SPEC.md\`, sección Fuentes permitidas).    
\- Consecuencia: si no se define, el WOW se vuelve humo. Si se define mal, se vuelve riesgo legal/confianza.

\---

\#\# 7\) Modelo de valor: por qué alguien deja WhatsApp/email  
\*\*DECIDIDO:\*\* Lead ≠ llamada. Opt-in se justifica por continuidad.

\*\*Valor que el usuario percibe (continuidad):\*\*  
\- Guardar el resultado para revisarlo después (sin perderlo).  
\- Compartirlo fácilmente con pareja/familia.  
\- Mantener una shortlist de finalistas.

\*\*ABIERTO (forma de opt-in):\*\*  
\- WhatsApp, email o ambos.    
\- Consecuencia: ambos suben conversión de captura, pero aumentan trabajo operativo; V1 debe priorizar mínimo viable sin dañar UX.

\---

\#\# 8\) Segmentación por intención (frío / tibio / caliente) y progresión  
\*\*Frío (curioso, exploración):\*\*  
\- Quiere comparar por emoción.  
\- Acción típica: hace 1 duelo y se va.  
\- Objetivo del sistema: darle un “wow” real y motivar guardar/compartir (continuidad).

\*\*Tibio (ya está decidiendo):\*\*  
\- Compara 2–4 propiedades seriamente.  
\- Acciones típicas: guarda, comparte, arma shortlist.  
\- Aquí aparece readiness gate.

\*\*Caliente (listo para ejecutar):\*\*  
\- Quiere visitar/ofertar/avanzar.  
\- Acciones típicas: completa readiness y pide siguiente paso humano.  
\- Regla: el sistema solo empuja humano si califica.

\*\*Movimiento de etapa (regla simple):\*\*  
\- Frío → Tibio: cuando el usuario busca continuidad (guardar/compartir/shortlist).    
\- Tibio → Caliente: cuando además supera readiness gate y pide siguiente paso.

\---

\#\# 9\) Métricas (30 días) \+ eventos que las alimentan  
\*\*Métrica principal (DECIDIDO por enfoque):\*\*  
\- % de usuarios que completan duelo y hacen continuidad (guardar o compartir).

\*\*Secundarias:\*\*  
\- % opt-in después del resultado (para guardar/compartir/shortlist).  
\- % readiness completado y “handoff” solicitado (solo usuarios calificados).

\*\*Eventos que alimentan métricas (nombres conceptuales; la lista detallada vive en \`TECH\_SPEC.md\`):\*\*  
\- duel\_started, duel\_completed, result\_viewed  
\- save\_clicked, share\_clicked, shortlist\_created  
\- optin\_started, optin\_completed  
\- readiness\_started, readiness\_completed  
\- handoff\_requested

\---

\#\# 10\) Riesgos de confianza y cómo se protegen  
\*\*Riesgos típicos:\*\*  
\- Números “demasiado exactos” sin fuente.  
\- Pedir teléfono antes de entregar valor.  
\- Inventar datos cuando faltan.  
\- Afirmaciones fuertes sin evidencia (cash-only/financeable).  
\- Contradicciones internas (cambios de criterio sin registrarlos).

\*\*Defensas (DECIDIDO / reglas):\*\*  
\- Disclaimers visibles: estimaciones/rangos \+ supuestos.  
\- “Faltan datos \= baja confianza” (regla obligatoria).  
\- No pedir PII antes del resultado.  
\- No afirmar cash-only/financeable sin evidencia verificable.  
\- Anti-drift: cambios solo con \`DECISION\_LOG.md\` \+ slices (\`CURRENT\_SLICE.md\`) \+ WIP=1.

\---

\#\# 11\) Supuestos ABIERTO (hipótesis) \+ validación sin construir todo  
\> Regla: si es ABIERTO, no se debate infinito; se valida con evidencia mínima.

1\) \*\*ABIERTO:\*\* Input V1 (2 links vs 2 direcciones).    
   \- Opciones:    
     \- O1: 2 direcciones (menos riesgo de scraping).    
     \- O2: 2 links, pero solo como “copia y pega datos mínimos” cuando falte data.    
   \- Validación mínima: entrevistas 1:1 \+ prueba con 10 personas (¿cuál completan sin ayuda?).

2\) \*\*ABIERTO:\*\* Qué “WOW” es dominante para buyers latinos (tax reset vs seguro vs flood vs condo friction).    
   \- Validación mínima: entrevistas 10–15 (capturar frases literales) antes de ajustar énfasis.

3\) \*\*ABIERTO:\*\* WhatsApp vs email como opt-in principal.    
   \- Validación mínima: prueba de preferencia en entrevistas \+ observar qué comparten (pareja/familia → WhatsApp suele ganar).

4\) \*\*ABIERTO:\*\* Granularidad local (condado vs más fino).    
   \- Validación mínima: con datos públicos reales disponibles, medir cuántas veces faltaría data (si falta demasiado, baja valor).

5\) \*\*ABIERTO:\*\* Readiness gate mínimo (3–5 preguntas) y su umbral para “pasar a humano”.    
   \- Validación mínima: revisar 20 conversaciones reales (o simuladas con leads reales) y ver tasa de “C que pide humano”.

\---

\#\# 12\) Referencias internas (docs del repo)  
\- \`PROJECT\_CHARTER.md\` — resumen ejecutivo y límites    
\- \`SYSTEM\_MAP.md\` — mapa del sistema    
\- \`WORKFLOW\_RULES.md\` — reglas anti-drift y autoridad de /docs    
\- \`DECISION\_LOG.md\` — decisiones y su “no reabrir hasta”    
\- \`CURRENT\_SLICE.md\` — slice activo y gate de cierre    
\- \`PARKING\_LOT.md\` — ideas pospuestas con fecha y gate

