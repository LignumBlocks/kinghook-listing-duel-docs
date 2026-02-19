# Master Project Checklist — KingHook (Listing Duel)

## VISIÓN GENERAL

### Objetivo del producto

KingHook es una herramienta especializada para compradores de vivienda en Miami-Dade y Broward que permite comparar dos propiedades (A vs B) para determinar cuál es la mejor opción y cuál es su "trampa principal" (riesgo o costo oculto). El enfoque es reducir sorpresas financieras y operativas mediante estimaciones transparentes, rangos y disclaimers claros, sin requerir datos personales de entrada.

### Alcance V1

- Comparación de 2 propiedades (Duelo A vs B).
- Veredicto basado en "trampas principales" (Taxes, Insurance, Flood, Condo friction).
- Resultado inmediato con niveles de confianza y disclaimers.
- Persistencia por continuidad (Guardar/Compartir/Shortlist).
- Gate de calificación (Readiness Gate) para filtrar leads de alta calidad.

### Qué NO es el producto

- NO es un buscador de propiedades (Zillow/Redfin killer).
- NO es asesoría legal, financiera o tributaria.
- NO garantiza exactitud total (usa rangos y supuestos).
- NO realiza scraping automático de portales privados.
- NO es para vendedores (sellers) en esta fase.

---

## ROADMAP POR FASES (A–Z)

### Fase 0 — SoT Setup (CERRADA)

- **Objetivo:** Establecer el repositorio como Fuente de Verdad (SoT) con reglas anti-drift.
- **In scope:** Creación de /docs base, log de decisiones y board inicial.
- **Out of scope:** Desarrollo de código o integraciones.
- **Done:** Repo legible en 3 min, docs coherentes, board con WIP=1.

### Fase 1 — Entrada Duelo mínima (ACTUAL)

- **Objetivo:** Capturar la entrada básica de dos propiedades.
- **In scope:** UI de entrada (form/links), persistencia mínima (Local Storage), navegación básica.
- **Out of scope:** Lógica de veredicto, normalización avanzada, enriquecimiento.
- **Done:** Demo donde se ingresan 2 propiedades y los datos persisten al refrescar.

### Fase 2 — Normalizador básico

- **Objetivo:** Transformar inputs heterogéneos en datos comparables.
- **In scope:** Contrato PropertyCandidate, mapeo de campos comunes, marcador de "data faltante".
- **Out of scope:** Extracción automática de fuentes externas, scoring.
- **Done:** Sistema que recibe 2 inputs y genera 2 objetos con estructura idéntica.

### Fase 3 — Motor del Duelo (veredicto + trampa)

- **Objetivo:** Implementar la lógica de decisión central.
- **In scope:** Lógica de comparación A vs B, identificación de trampa principal, cálculo de confianza.
- **Out of scope:** UI final de reporte, compartición social.
- **Done:** Función/Módulo que devuelve un ganador y la razón principal del riesgo.

### Fase 4 — Resultado con confianza y disclaimers

- **Objetivo:** Presentar el veredicto de forma transparente y segura.
- **In scope:** Pantalla de resultado, visualización de rangos, disclaimers dinámicos por falta de data.
- **Out of scope:** Opt-in de lead, registro de contacto.
- **Done:** El usuario ve el ganador, entiende el riesgo y conoce las limitaciones de los datos.

### Fase 5 — Guardar / Compartir / Shortlist

- **Objetivo:** Validar el interés del usuario mediante la continuidad.
- **In scope:** Botones de acción, captura de canal (WhatsApp/Email), persistencia de comparaciones favoritas.
- **Out of scope:** Integración real con APIs de envío masivo.
- **Done:** El usuario puede "bloquear" un resultado dejándolo guardado u obteniendo un link único.

### Fase 6 — Readiness Gate

- **Objetivo:** Filtrar intención de compra real antes del contacto humano.
- **In scope:** Cuestionario de 3-5 preguntas, lógica de calificación A/B/C.
- **Out of scope:** Agendamiento automático de citas en calendario externo.
- **Done:** El sistema asigna un nivel de preparación al usuario basado en sus respuestas.

### Fase 7 — Conversión humana controlada

- **Objetivo:** Facilitar el paso al experto solo para perfiles calificados.
- **In scope:** Botón de "Hablar con experto" (solo para calificados), minimización de PII.
- **Out of scope:** Sistema de chat en vivo integrado.
- **Done:** Registro de solicitud de contacto de un usuario calificado.

### Fase 8 — Métricas y optimización

- **Objetivo:** Medir el éxito del MVP y ajustar el flujo.
- **In scope:** Implementación de Google Analytics / Mixpanel de eventos base.
- **Out of scope:** A/B testing complejo.
- **Done:** Dashboard que muestra conversión de Duelo a Continuidad.

---

## ESTADO ACTUAL

- **Slice activo:** Fase 1 — Entrada Duelo mínima.
- **Último slice cerrado:** Fase 0 — SoT Setup.
- **Qué NO se está tocando ahora:** Motor de scoring, integraciones de correo/WhatsApp, UI de resultados finales.
