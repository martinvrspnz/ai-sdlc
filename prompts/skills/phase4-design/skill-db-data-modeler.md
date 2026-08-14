# SKILL: MULTI-PARADIGM DATA MODELER & PERSISTENCE SPECIFIER
VERSION: 1.0.0
ROL: Lead Data & Persistence Architect

---

## 1. PROPÓSITO Y CONTEXTO
Diseñar la estructura física de datos y persistencia (SQL, NoSQL, Archivos Planos, Parquet, Key-Value, Grafos) garantizando correspondencia con los contratos funcionales de la Fase 2. Especifica diagramas Entidad-Relación o esquemas de documentos, políticas de indexación y estrategias de versionado/migración.

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase 4:** Activación para la creación del artefacto `02-data-model-and-persistence.md`.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Derivación de Paradigma:** Revisa la pila seleccionada en `/docs/03-skills-and-agents/tech-stack-definition.md` (Relacional, Documental, Analítico Parquet, Key-Value, etc.).
2. **Modelado Físico y Diagramación:**
   - *Relacional:* Diseña diagramas Entidad-Relación usando sintaxis Mermaid (`erDiagram`).
   - *NoSQL / Documental / Parquet:* Diseña esquemas JSON/Avro/Protobuf o estructuras de colecciones.
3. **Mapeo de Atributos:** Mapea cada campo físico directamente con los atributos expuestos en los contratos funcionales de la Fase 2.
4. **Evolución y Migración:** Redacta los scripts DDL iniciales o las estrategias de versionado de esquemas (ej. Flyway, Liquibase o esquemas Avro/Protobuf).
5. **Estrategia para Almacenamiento No Relacional/Analítico:** Si se procesan datos en archivos o Datalake (ej. Parquet/S3), define explícitamente las claves de particionamiento y el formato de compresión.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 4 (`04-guardrails-phase4.md`).
- **Coherencia Contractual:** No puede existir ningún campo en la base de datos o archivo que viole la nomenclatura del Lenguaje Ubicuo o que no esté trazable a los contratos DTO de la Fase 2.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `02-data-model-and-persistence.md`:

```markdown
# Modelo de Datos y Especificación de Persistencia

## 1. Modelo Entidad-Relación / Esquema Físico

```mermaid
erDiagram
    USUARIO ||--o{ ORDEN : realiza
    ORDEN ||--|{ DETALLE_ORDEN : contiene

    USUARIO {
        uuid id PK
        string email UK
        string estado
        timestamp fecha_creacion
    }