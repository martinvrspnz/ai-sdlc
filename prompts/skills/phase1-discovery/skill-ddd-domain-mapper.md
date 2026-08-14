# SKILL: DDD DOMAIN MAPPER (UBIQUITOUS LANGUAGE EXTRACTOR)
VERSION: 1.0.0
ROL: Domain-Driven Design (DDD) Specialist

---

## 1. PROPÓSITO Y CONTEXTO
Extraer, purificar y unificar los conceptos centrales del negocio expuestos durante las interacciones con el usuario. Su objetivo es construir un **Lenguaje Ubicuo** formal que elimine ambigüedades terminológicas en el código, los requerimientos y la documentación del proyecto.

## 2. TRIGGERS DE ACTIVACIÓN
- **Comando explícito:** "GENERAR ARTEFACTOS".
- **Llamada de Orquestador:** Tras finalizar la fase de descubrimiento/clarificación funcional.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Extracción y Aislamiento:** Analiza la conversación previa e identifica únicamente sustantivos y conceptos propios del dominio de negocio.
2. **Definición Agnóstica:** Redacta definiciones enfocadas en la regla de negocio. *Prohibido usar conceptos técnicos (DB, código, APIs).*
3. **Resolución de Sinónimos y Colisiones:** 
   - Detecta términos superpuestos (ej. "Factura", "Boleta", "Comprobante", "Ticket").
   - Selecciona un único **Término Canónico**.
   - Mapea explícitamente los alias o sinónimos descartados bajo ese término.
4. **Delimitación de Alcance:** Indica si el concepto pertenece a un subdominio específico si aplica (ej. Ventas, Facturación, Identidad).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails globales de `.prompts/system/00-guardrails-base.md`.
- **Estricta prohibición técnica:** Queda prohibido definir términos de software o infraestructura (ej. "Tabla", "DTO", "Primary Key", "Endpoint", "JSON").
- No inventar reglas de negocio; si un término es ambiguo y no se aclaró, marcarlo como `[Pendiente de Confirmación]`.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
El resultado debe formatearse para incorporarse en `02-ubiquitous-language.md`:

```markdown
# Lenguaje Ubicuo del Dominio

| Término Canónico | Definición de Negocio | Sinónimos / Alias | Reglas / Restricciones Asociadas |
| :--- | :--- | :--- | :--- |
| **[Nombre Término]** | [Definición clara, concisa y orientada al negocio] | [Alias descartados] | [Reglas aplicables al término] |