# Current Slice — Slice 6 (Historial + Export del Duelo)

## Slice 6 — Objetivo

Permitir que el usuario vea, recupere y exporte duelos recientes (inputs + supuestos + resultado), sin integraciones externas.

## In scope

- Persistir el último duelo y un historial corto (ej. 10–20) en almacenamiento local (localStorage).
- UI mínima: sección "Historial" con lista de duelos recientes y botón "Cargar" para re-hidratar A/B y costos.
- Exportar un duelo a JSON (descarga o "copiar JSON").
- Mantener el output final intacto: winner + costo real estimado (rango) + trampa dominante + razones (máx 5) + disclaimers.

## Out of scope (prohibido en este slice)

- Cuentas, login, backend, base de datos.
- Integraciones externas / scraping / calls a Zillow/Redfin.
- Nuevos modelos de costos o nuevos campos del contrato.
- Modo "seller", CMA, o cualquier cosa fuera del buyer flow.

## Done checklist (demo funcional de Slice 6)

- [ ] Hago un duelo, refresco la página y el último duelo se restaura (A/B + costos + resultado).
- [ ] Veo un historial (máx 20) y puedo cargar cualquiera al estado actual.
- [ ] Puedo exportar el duelo seleccionado a JSON (descarga o copiar al clipboard).
- [ ] No se rompe ningún test existente (normalizer/duel_engine/ui_renderer/cost_model).

## Regression checklist

- [ ] WIP=1: solo Slice 6 en Now.
- [ ] Contratos PropertyCandidate/DuelResult no cambian.
- [ ] Ideas nuevas van a Parking Lot con fecha/motivo.

## Gate para cerrar Slice 6

- Demo en browser: crear duelo → aparece en historial → refrescar → se restaura → export JSON funciona.
- Evidencia: comando + output de un smoke manual + lista de archivos tocados + commit SHA en DECISION_LOG.

# Siguiente slice: por definir (Slice 7)
