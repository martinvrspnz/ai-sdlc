# PROMPT DE SÍNTESIS INICIAL PARA NOTEBOOKLM (DISCOVERY INPUT)
VERSION: 2.0.0
APLICACIÓN: Entrada inicial de análisis en NotebookLM para la Fase 1 (Discovery)
PROCESO DESTINO: Insumo directo para `.prompts/system/phase/01-phase1-discovery.md`

---

## 1. OBJETIVO Y PROPÓSITO
Analizar exhaustivamente todas las fuentes de información del cliente cargadas en este cuaderno de NotebookLM (documentos de requerimientos, transcripciones de reuniones, audios, enlaces, notas de negocio, diagramas) para sintetizar y consolidar un **Resumen Ejecutivo de Negocio** estructurado que sirva de punto de partida para la fase de descubrimiento y clarificación funcional.

## 2. INSTRUCCIONES DE EJECUCIÓN
Extrae de manera quirúrgica la información relevante contenida en los materiales subidos y organízala en las secciones obligatorias detalladas en la estructura de salida.

## 3. GUARDRAILS DE CONTENIDO, ÉTICA Y TONO PROFESIONAL
- **Tono Institucional:** Mantén en todo momento un tono estrictamente profesional, corporativo, neutro y objetivo.
- **Filtro de Contenido:** Concéntrate EXCLUSIVAMENTE en la solución de software y las necesidades del negocio. Ignora, descarta y omite cualquier comentario, nota o alusión fuera de contexto (temas políticos, religiosos, ideológicos, bélicos, racistas, sexistas o discriminatorios).
- **Lenguaje Limpio:** Queda estrictamente prohibido incluir palabras ofensivas, agresivas, sarcásticas, modismos soeces o groserías de cualquier tipo.
- **Cero Asunciones en Negocio:** Si la documentación subida no especifica un proceso o regla de negocio, colócalo explícitamente en la sección de "Puntos Oscuros / Gaps", en lugar de inventar la solución.

---

## 4. ESTRUCTURA Y FORMATO DE SALIDA REQUERIDO

Consolida el informe de análisis aplicando exactamente la siguiente plantilla en Markdown:

```markdown
# Resumen Ejecutivo de Descubrimiento de Negocio

## 1. RESUMEN EJECUTIVO DE LA IDEA
* [Explicación detallada en 2 o 3 párrafos sobre qué es la solución tecnológica planteada, cuál es el valor que aporta y qué problema o necesidad principal del negocio busca resolver].

---

## 2. USUARIOS Y STAKEHOLDERS IDENTIFICADOS
* Lista detallada de perfiles de usuario, roles y actores de negocio identificados que interactuarán directa o indirectamente con la solución (ej. Cliente Final, Administrador de Sistema, Operador Logístico, Auditor, etc.).

---

## 3. REQUISITOS Y REGLAS DE NEGOCIO MENCIONADOS
* Lista puntual y detallada de todas las características, procesos, flujos, capacidades o reglas operativas explicitadas en las fuentes de información.

---

## 4. RESTRICCIONES TÉCNICAS U OPERATIVAS
* Lista de todas las limitaciones explicitadas en los insumos (ej. plazos de entrega, integraciones obligatorias con sistemas de terceros, normativas legales/tributarias aplicables, presupuestos, límites operativos).

---

## 5. PUNTOS OSCUROS O INFORMACIÓN FALTANTE (GAPs)
* Lista explícita y pormenorizada de temas ambiguos, inconsistencias entre fuentes, vacíos funcionales o aspectos no explicados en los materiales subidos que requieren aclaración prioritaria.