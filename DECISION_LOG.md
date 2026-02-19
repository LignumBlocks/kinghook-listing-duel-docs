# KingHook (Listing Duel) — Decision Log

## Regla (para que el log no muera)  

- “No reabrir hasta” debe ser una condición concreta (ej: “hasta cerrar Slice X” o “hasta tener N usos reales”).  
- EXCEPCIÓN: decisiones “constitucionales” (SoT, WIP=1, 1 Project) pueden decir “hasta V1 cerrada”.

## Plantilla (cada decisión)  

- Fecha (YYYY-MM-DD):  
- Decisión:  
- Motivo (1–3 bullets):  
- Impacto (qué cambia / qué habilita):  
- No reabrir hasta (condición concreta):  
- Notas (opcional):

---

## Slice 6 — Activación

- Fecha: 2026-02-19
- Decisión: Activar Slice 6 — Historial + Export del Duelo.
- Motivo:
  - Completa el flujo buyer: recuperar y comparar duelos sin repetir inputs.
- Impacto:
  - Mejora UX sin tocar contratos ni agregar integraciones externas.
- No reabrir hasta: Slice 6 cerrado (Gate cumplido con evidencia).

---

## Decisiones constitucionales (DECIDIDO)

- Fecha: 2026-02-17  
- Decisión: Fuente de Verdad (SoT) = GitHub.  
- Motivo:  
  - Evitar pérdida de contexto.  
  - Historial y control de cambios.  
- Impacto:  
  - Todo acuerdo vive en /docs e se actualiza por commits.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: Un solo Project para todo el trabajo.  
- Motivo:  
  - Evitar dispersión.  
- Impacto:  
  - Un tablero, una prioridad, un slice activo.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: Dolor principal = olvido de contexto.  
- Motivo:  
  - Si se pierde el hilo, el proyecto deriva.  
- Impacto:  
  - Docs obligatorios + log de decisiones + slice claro.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: WIP = 1 (solo un slice activo).  
- Motivo:  
  - Reducir drift e multitarea.  
- Impacto:  
  - Lo demás va al Parking Lot.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: Prioridad solo cambia al cerrar slice.  
- Motivo:  
  - Evitar saltos por ansiedad o ideas nuevas.  
- Impacto:  
  - “Lo nuevo” no interrumpe; se estaciona.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: “Cerrado” = demo funcional.  
- Motivo:  
  - Evitar “casi listo”.  
- Impacto:  
  - Cada slice tiene gate verificable.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: Parking Lot automático para variaciones/mejoras/ideas.  
- Motivo:  
  - Capturar ideas sin desviar el trabajo.  
- Impacto:  
  - Nada se pierde y nada interrumpe.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-17  
- Decisión: Drive opcional solo para apoyo.  
- Motivo:  
  - Mantener SoT único.  
- Impacto:  
  - El repo manda; Drive solo referencia.  
- No reabrir hasta: V1 cerrada.

- Fecha: 2026-02-18  
- Decisión: Cierre formal de Slice 0 (SoT Setup).  
- Motivo:  
  - Documentación base completada y verificada.  
  - Reglas de operación establecidas y coherentes.  
  - Board operativo inicializado con WIP=1.  
- Impacto:  
  - El repositorio es la Fuente de Verdad (SoT).  
  - Se habilita el avance a Slice 1 tras validación.  
- No reabrir hasta: V1 cerrada.

---

### Snapshot del Project “KingHook” (2026-02-18)

- **Now** (WIP=1): 1
  - Finalizar Cierre de Slice 0.
- **Next**: 1
  - Inicio de Slice 1 (Setup de Arquitectura/App Skeleton).
- **Done**: 4
  - Estructuración de /docs (6+ archivos base).
  - Definición de decisiones constitucionales.
  - Configuración de Board y reglas de trabajo.
  - Carga inicial de Parking Lot (5 items).
- **Parking Lot**: 5
  - (Ver /docs/PARKING_LOT.md)

- Fecha: 2026-02-18  
- Decisión: Inicio de Slice 1 (Entrada Duelo mínima).  
- Motivo:  
  - Slice 0 cerrado formalmente.  
  - Necesidad de validar la captura de datos antes de lógica compleja.  
- Impacto:  
  - Se inicia el desarrollo técnico (App Skeleton + UI de entrada).  
  - El foco es persistencia y UI básica, no inteligencia.  
- No reabrir hasta: Gate de Slice 1 cerrado.

---

### Snapshot del Project “KingHook” (2026-02-18 - Activación Slice 1)

- **Now** (WIP=1): 1
  - Slice 1 — Entrada Duelo mínima.
- **Next**: 2
  - Slice 2 — Motor del Duelo (Veredictos).
  - Implementación de Normalizador.
- **Done**: 5
  - Estructuración de /docs (6+ archivos base).
  - Definición de decisiones constitucionales.
  - Configuración de Board y reglas de trabajo.
  - Carga inicial de Parking Lot (5 items).
  - Cierre formal de Slice 0 (SoT Setup).
- **Parking Lot**: 5
  - (Ver /docs/PARKING_LOT.md)

---

- Fecha: 2026-02-18  
- Decisión: Cierre formal de Slice 1 (Entrada Duelo mínima).  
- Motivo:  
  - UI de entrada A/B funcional y verificada en test local (localhost:5173).  
  - Persistencia en localStorage (key: kinghook.duel.draft) confirmada.  
  - Validación de inputs y vista placeholder de procesamiento operativa.  
- Impacto:  
  - Se habilita el avance a Slice 2 (Normalizador básico).  
  - El formulario de entrada queda como base para el flujo completo.  
- No reabrir hasta: V1 cerrada.

---

### Snapshot del Project "KingHook" (2026-02-18 - Cierre Slice 1)

- **Now** (WIP=1): 1
  - Slice 2 — Normalizador básico.
- **Next**: 1
  - Slice 3 — Motor del Duelo.
- **Done**: 6
  - Estructuración de /docs (6+ archivos base).
  - Definición de decisiones constitucionales.
  - Configuración de Board y reglas de trabajo.
  - Carga inicial de Parking Lot (5 items).
  - Cierre formal de Slice 0 (SoT Setup).
  - Cierre formal de Slice 1 (Entrada Duelo mínima).
- **Parking Lot**: 5
  - (Ver /docs/PARKING_LOT.md)

---

- Fecha: 2026-02-18  
- Decisión: Cerrar Slice 2 — Normalizador básico (PropertyCandidate + normalizer + tests).  
- Motivo:  
  - Contract mínimo definido (9 campos, sin extras).  
  - Normalizer implementa URL/ZIP/City/State best-effort.  
  - missing_fields consistente: lista keys cuyo valor es null.  
  - Confidence per-field (city/state/zip: "low" | "unknown").  
  - Tests node+assert pasan sin dependencias (25/25 OK).  
- Evidencia: PR #7 mergeado a main (squash). Commit main: cf3216680a70f4133de41b4709bccedd96ed6b44.  
- Impacto:  
  - Habilita Slice 3 (Enrichment permitido) sobre PropertyCandidate estable.  
  - El contrato queda como base para el motor del duelo.  
- No reabrir hasta: Si Slice 3 requiere campos nuevos, se propone y se decide explícitamente en /docs antes de tocar el contrato.

---

- Fecha: 2026-02-18  
- Decisión: SoT mirror público de /docs para visibilidad del asistente.  
- Motivo:  
  - Repo principal (kinghook-listing-duel) permanece privado.  
  - Se necesita visibilidad de /docs sin exponer código fuente.  
- Impacto:  
  - Repo público: LignumBlocks/kinghook-listing-duel-docs (solo archivos de /docs).  
  - No contiene código, solo documentación SoT.  
  - Sincronización automática vía GitHub Action (.github/workflows/docs-mirror.yml) en cada push a main que toque /docs.  
  - Requiere secret DOCS_MIRROR_PAT con scope repo en el repo privado.  
- No reabrir hasta: V1 cerrada.  
- Nota: DOCS_MIRROR_PAT configurado y sync automático activado (2026-02-18).

---

- Fecha: 2026-02-18  
- Decisión: Cerrar Slice 3 — Motor del Duelo (DuelResult engine + tests).  
- Motivo:  
  - Motor DuelResult honesto implementado (winner=cannot_determine sin datos de costo/riesgo).  
  - Alineado con TECH_SPEC 6.2: disclaimers = solo referencias, missing_data ≤ 10.  
  - Tests sin dependencias: duel_engine 19/19 + normalizer 25/25 reproducibles.  
- Evidencia: PR #8 mergeado (squash) a main. Commit main: 80d74ed.  
- Impacto:  
  - Habilita Slice 4 — Resultado con confianza y disclaimers.  
  - Contratos PropertyCandidate (9 keys) y DuelResult (7 keys) estables.  
- No reabrir hasta: Si Slice 4 exige cambiar contratos, decidir en /docs antes de tocar código.

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: Permitir export mínimo a `window` en normalizer.js y duel_engine.js para habilitar UI sin bundler.
- Motivo (1–3 bullets):
  - La UI (Slice 4) requiere acceso en browser a `normalizeCandidate` y `scoreDuel` sin imports.
  - Mantener stack-agnostic (sin bundler) y sin tocar contratos/lógica.
  - Node tests siguen intactos (exports por module.exports).
- Impacto (qué cambia / qué habilita):
  - Habilita el flujo end-to-end en browser cargando scripts por orden.
- No reabrir hasta (condición concreta):
  - Hasta que exista una migración verificada a imports ES modules (o bundler) y se eliminen estos `window exports` en un commit con tests PASS.
- Notas (opcional):
  - Cambio fue solo guards `if (typeof window !== 'undefined')` (4 líneas normalizer, 3 líneas duel_engine).

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: Cerrar Slice 4 — Resultado con confianza y disclaimers.
- Motivo (1–3 bullets):
  - Flujo end-to-end funcional: input → normalizeCandidate → scoreDuel → renderDuelResultToHTML.
  - UI renderiza 7 secciones y mantiene el contrato (disclaimers = ["TECH_SPEC#11"]).
  - Gates reproducibles: normalizer 40/40 + duel_engine 19/19 + ui_renderer PASS; smoke Caso A/B OK.
- Impacto (qué cambia / qué habilita):
  - UI mínima lista para continuar con el siguiente slice (definir Slice 5).
- No reabrir hasta (condición concreta):
  - Hasta que el Gate de Slice 5 esté definido y se demuestre que Slice 5 exige cambiar contratos (entonces: decisión previa en /docs antes de tocar código).
- Notas (opcional):
  - Evidencia: PR #9 (HEAD 6615436). Tests: normalizer 40/40, duel_engine 19/19, ui_renderer PASS.
  - Smoke actualizado: URLs con slug (-Miami-FL-33155, -Fort-Lauderdale-FL-33301) ya extraen city/state/zip; missing_data solo costos + address_text; TECH_SPEC#11 visible.

### Snapshot del board al cierre de Slice 4

- **Now (WIP=1):** (vacío — pendiente definir Slice 5)  
- **Next:** TBD  
- **Done:** Slice 0, Slice 1, Slice 2, Slice 3, Slice 4  
- **Parking Lot:** ver /docs/PARKING_LOT.md

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: Abrir Slice 5 — Costo real estimado (rango). Costo = solo rangos ingresados por el usuario.
- Motivo (1–3 bullets):
  - El motor necesita datos de costo para dejar de devolver `cannot_determine` siempre.
  - Sin scraping ni APIs: el usuario ingresa rangos de HOA, taxes, insurance, maintenance, utilities, mortgage P&I.
  - Regla de winner: si rangos de costo mensual total no se solapan → menor costo gana con `confidence=media`. Si solapan >20% del rango menor → `cannot_determine`. Umbral de 20% documentado aquí.
- Impacto (qué cambia / qué habilita):
  - `scoreDuel` acepta parámetros opcionales de costo sin romper el flujo sin costos (backward-compatible).
  - PropertyCandidate (9 keys) y DuelResult (7 keys) intactos. Costos viajan como parámetros separados.
- No reabrir hasta (condición concreta):
  - Hasta que Slice 6 esté definido o se hayan procesado 20 duelos reales con costos.
- Notas (opcional):
  - Componentes: HOA (mo), Taxes (yr→mo), Insurance (yr→mo), Maintenance (mo), Utilities (mo), Mortgage P&I (mo).
  - Conversión automática: /yr → /12. parseRange soporta "$200-$350", "300", "3600/yr".

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: Cerrar Slice 5 — Costo real estimado (rango).
- Motivo (1–3 bullets):
  - cost_model.js implementado: parseRange + estimateMonthlyCostRange con 6 componentes y yr→mo.
  - scoreDuel extendido con 3 params opcionales (costA, costB, mortgage). Winner logic con umbral de solapamiento 20%.
  - Gates en main (`6390b6a`): normalizer 40/40, duel_engine 36/36, ui_renderer PASS, cost_model 20/20.
- Impacto (qué cambia / qué habilita):
  - El motor puede determinar un ganador cuando el usuario provee rangos de costo (confidence=baja porque flood_risk desconocido).
  - PropertyCandidate (9 keys) y DuelResult (7 keys) intactos. Backward-compatible.
- No reabrir hasta (condición concreta):
  - Hasta que Slice 6 esté definido o se hayan procesado 20 duelos reales con costos.
- Notas (opcional):
  - PRs: #10 (main `181714e`) + #11 refinamiento (main `6986a9c`). Docs: main `6390b6a`.
  - Refinamiento: list_price removido de CRITICAL_COST_FIELDS, flood_risk reduce confianza (media→baja) y setea primary_trap, 3 decisiones explícitas (A/B/C) documentadas.
  - Smoke (a): no-solape A $1000 vs B $1600 → winner=A, confidence=baja (flood_risk), primary_trap="Riesgo de inundación desconocido". TECH_SPEC#11 visible.
  - Smoke (b): solape 100% → cannot_determine con rangos visibles en reasons. TECH_SPEC#11 visible.

### Snapshot del board al cierre de Slice 5

- **Now (WIP=1):** (vacío — pendiente definir Slice 6)
- **Next:** TBD
- **Done:** Slice 0, Slice 1, Slice 2, Slice 3, Slice 4, Slice 5
- **Parking Lot:** ver /docs/PARKING_LOT.md

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: (A) Umbral de solape = 20% del rango menor.
- Motivo (1–3 bullets):
  - ratio_solape = overlap_length / min(rangoA, rangoB). Si ≤ 0.20 → menor midpoint gana con confidence=baja. Si > 0.20 → cannot_determine.
  - Umbral elegido como balance entre utilidad y honestidad: 20% permite diferencias suficientes sin inventar certeza.
- Impacto (qué cambia / qué habilita):
  - Regla determinista para convertir rangos en winner o cannot_determine con código reproducible.
- No reabrir hasta (condición concreta):
  - Hasta que 20 duelos reales muestren que el umbral produce resultados inadecuados (evidencia en analytics o feedback de usuarios).

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: (B) list_price NO requerido si el usuario provee P&I mensual (rango) o si la comparación es solo costos no-hipoteca.
- Motivo (1–3 bullets):
  - Slice 5 compara costo mensual de propiedad, no precio de compra.
  - Si el usuario da HOA, taxes, insurance y opcionalmente P&I, el rango mensual se puede calcular sin list_price.
  - Eliminar list_price de CRITICAL_COST_FIELDS evita falsos positivos en missing_data.
- Impacto (qué cambia / qué habilita):
  - missing_data ya no lista list_price como campo crítico faltante.
- No reabrir hasta (condición concreta):
  - Hasta que un slice futuro requiera comparar precio de compra o calcular hipoteca desde list_price (entonces agregar como campo separado con decisión previa en /docs).

---

- Fecha (YYYY-MM-DD): 2026-02-18
- Decisión: (C) flood_risk NO bloquea ganador por costo; reduce confianza y puede ser primary_trap.
- Motivo (1–3 bullets):
  - Si hay rangos de costo suficientes, el motor puede declarar ganador por costo. flood_risk es un factor de riesgo adicional, no un bloqueador.
  - Si flood_risk falta: confidence baja 1 nivel (media→baja) y primary_trap menciona "riesgo de inundación desconocido".
  - Esto mantiene honestidad sin forzar cannot_determine cuando hay datos de costo claros.
- Impacto (qué cambia / qué habilita):
  - El motor puede dar winner != cannot_determine cuando hay costos, aun sin flood_risk. La falta de flood_risk queda visible en missing_data y primary_trap.
- No reabrir hasta (condición concreta):
  - Hasta que un slice integre una fuente verificable de flood_risk (FEMA maps o similar) y se pueda incorporar como factor de decisión con tests.
