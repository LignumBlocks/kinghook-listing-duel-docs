\# Workflow Rules — KingHook (anti-drift)

\#\# Reglas operativas (resumen)  
\- DECIDIDO: Fuente de Verdad (SoT) \= GitHub.  
\- DECIDIDO: Un solo Project (un solo tablero).  
\- DECIDIDO: WIP \= 1 (solo un slice activo).  
\- DECIDIDO: La prioridad solo cambia al cerrar slice.  
\- DECIDIDO: “Cerrado” \= demo funcional (gate verificable).  
\- DECIDIDO: Cualquier idea nueva → Parking Lot (automático).  
\- Drive es opcional y solo apoyo; el repo manda.

\#\# Regla de oro contra contradicciones  
\- Si hay contradicción, gana /docs.  
\- Si algo no está escrito en /docs, no está decidido.

\#\# Cómo usar el repo como verdad (8 bullets)  
\- Todo acuerdo vive en /docs (no en chats).  
\- Cada cambio de dirección requiere una entrada en DECISION\_LOG.  
\- CURRENT\_SLICE define qué se hace ahora; lo demás va al Parking Lot.  
\- WIP=1 siempre: una cosa activa, el resto espera.  
\- Para cerrar un slice: cumplir el Gate de CURRENT\_SLICE.  
\- Solo al cerrar slice se puede cambiar prioridad (Next → Now).  
\- El tablero refleja el estado real (Now/Next/Done/Parking Lot).  
\- Si un tema no cabe en el slice actual, se registra y se pospone (no se improvisa).

\#\# Gate estándar (para cerrar slices)  
\- Checklist “Done” completo.  
\- Sin contradicciones entre docs.  
\- El tablero coincide con la realidad.

## Cierre formal de slice (obligatorio)

Un slice NO está cerrado hasta que:

- Gate marcado en CURRENT_SLICE.md
- Entrada de cierre en DECISION_LOG.md
- BOARD_STATE.md actualizado
- Todo mergeado en main

Validaciones por copy-paste no son válidas.
Solo main es auditable.
