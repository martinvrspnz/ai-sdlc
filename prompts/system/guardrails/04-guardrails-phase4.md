# GUARDRAILS ESPECÍFICOS - FASE 4: ARQUITECTURA, MODELADO E INFRAESTRUCTURA
VERSION: 2.0.0
APLICACIÓN: Fase 4 (Blueprint de Arquitectura de Software, Modelado de Datos y Persistencia, Estrategia Integral de Testing y Topología de Infraestructura/Despliegue)
PREVALENCIA: Se aplican de forma obligatoria durante el diseño del Blueprint de Arquitectura, Modelado de Datos, Estrategia de Testing y Topología de Infraestructura en la Fase 4. Complementan a los guardrails base (`00-guardrails-base.md`) y a las especificaciones aprobadas en las Fases 2 y 3.

---

## 1. ALINEAMIENTO ABSOLUTO AL STACK TECNOLÓGICO Y FIDELIDAD A FASES PREVIAS
- **Derivación Estricta:** Todas las decisiones de arquitectura, selección de frameworks, herramientas de persistencia, contenedores, orquestadores, infraestructura cloud y herramientas de testing deben derivarse ESTRICTAMENTE de la definición del stack tecnológico (`/docs/03-skills-and-agents/tech-stack-definition.md`).
- **Prohibición de Componentes Extraños:** Queda prohibido introducir librerías, bases de datos, middlewares, componentes o servicios de infraestructura que no estén explícitamente declarados o justificados en el stack técnico del proyecto.
- **Trazabilidad sin Sobreingeniería (Zero Over-engineering):** Todo componente, módulo o servicio diseñado en esta fase debe vincularse directamente a una Historia de Usuario `[US-XX]` o Contrato Funcional de la Fase 2.

## 2. MODELADO DE ARQUITECTURA ESTÁNDAR (C4 MODEL & MERMAID)
- **Modelo C4 Obligatorio:** El diseño arquitectónico debe utilizar obligatoriamente el estándar **C4 Model** (Nivel 1: Contexto, Nivel 2: Contenedores, Nivel 3: Componentes y, si aplica, Nivel 4: Código).
- **Diagramación parseable en Mermaid:** Todos los diagramas (diagramas C4, diagramas de secuencia, modelos Entidad-Relación, topología de redes y despliegue) deben redactarse única y exclusivamente en sintaxis **Mermaid** dentro de bloques de código Markdown parseables.
- **Delimitación de Responsabilidades:** Cada nivel del C4 Model debe describir con claridad la responsabilidad de las capas, los límites del sistema, los patrones de comunicación y los protocolos de integración entre componentes.

## 3. PATRONES DE DISEÑO Y DESACOPLAMIENTO (HEXAGONAL / CLEAN / ONION ARCHITECTURE)
- **Separación Rigurosa de Capas:** El código y la arquitectura deben organizarse respetando principios de separación de responsabilidades (Arquitectura Hexagonal / Ports & Adapters, Clean Architecture, Onion Architecture o DDD, según lo defina el stack del proyecto).
- **EL DOMINIO ES INMUTABLE Y AISLADO:** El núcleo de negocio (Domain Core) no debe depender bajo ningún concepto de detalles de infraestructura, frameworks (Quarkus/Spring), controladores, librerías externas o mecanismos de persistencia.
- **DESACOPLAMIENTO BASE DE DATOS - CONTRATO (Zero DB-to-API Leak):** Queda estrictamente PROHIBIDO exponer modelos físicos/internos de persistencia (ej. Entidades JPA/Panache, tablas SQL, documentos NoSQL) directamente en los contratos de API, DTOs de transporte o interfaces de presentación. Es obligatorio el uso explícito de patrones de mapeo (Mappers / Transformers) entre las capas de dominio, infraestructura y presentación.
- **Principios SOLID & Clean Code:** Los principios SOLID y las buenas prácticas de diseño deben aplicarse explícitamente a la estructura de paquetes, contratos de interfaz (Puertos) y abstracciones.

## 4. MODELADO DE PERSISTENCIA FLEXIBLE Y MULTI-PARADIGMA
- **Adaptabilidad de Persistencia:** El modelado de datos debe adaptarse rigurosamente al paradigma de persistencia seleccionado en el stack técnico (Relacional/SQL, NoSQL Documental, Key-Value, Archivos Planos, Columnar/Parquet, Grafo, Vectorial, etc.).
- **Persistencia Estructurada:** Para persistencia estructurada (SQL / NoSQL rígido), es obligatorio especificar los esquemas físicos, diagramas Entidad-Relación (`erDiagram`), estructuras de colecciones/documentos, estrategias de indexación y planes de migración de esquema versionados (Data Versioning/Migrations mediante Flyway o Liquibase).
- **Persistencia Analítica y de Archivos:** Para almacenamiento analítico o de archivos (Parquet, Data Lakes, Storage en GCP), se deben definir explícitamente las claves de particionamiento, esquemas de serialización, formatos de compresión (Snappy/GZIP) y políticas de retención de datos.

## 5. DISEÑO DE ARQUITECTURA Y VALIDACIÓN FORMAL DE RNF
- **Patrones de Resiliencia:** La arquitectura debe incorporar explícitamente patrones de resiliencia y alta disponibilidad (Circuit Breaker, Bulkhead, Rate Limiting, Retries, Caching, Autoscaling) necesarios para respaldar y garantizar los RNF definidos en la Fase 2.
- **Quality Gates de RNF:** En los artefactos `03-testing-strategy.md` y `04-infrastructure-and-deploy.md`, es obligatorio formalizar los Quality Gates de RNF (límites de latencia expresados en P95/P99, umbrales de throughput en TPS para pruebas de carga/estrés, políticas de trazabilidad distribuida con Trace ID y tolerancias de error).

## 6. ESTRATEGIA DE TESTING INTEGRAL Y COBERTURA MULTI-CAPA
- **Estructura de Pruebas:** La arquitectura debe incorporar una estrategia de Pruebas integral que responda a la estructura de capas elegida (Pirámide o Diamante de Testing).
- **Niveles de Prueba Obligatorios:** Se deben definir las pautas, herramientas y criterios de aceptación para los diferentes niveles de prueba aplicables:
  * **Pruebas Unitarias y de Dominio:** Aislamiento total de la lógica de negocio mediante Test Doubles (Mocks/Stubs).
  * **Pruebas de Integración y Contrato:** Verificación de base de datos en memoria o contenedores (Testcontainers), interfaces y servicios REST/Eventos.
  * **Pruebas de Carga / Estrés / Performance:** Validación de límites de throughput (TPS) y latencia bajo carga nominal y pico.
  * **Pruebas de Humo (Smoke Testing):** Verification suite ligera para validación rápida post-despliegue en ambientes de ejecución.
  * **Pruebas de Marcha Blanca / Stage:** Validación de escenarios completos de aceptación E2E con datos anonimizados en entornos pre-productivos.

## 7. INFRAESTRUCTURA, CONTENERIZACIÓN Y ESTRATEGIAS DE DESPLIEGUE
- **Soporte de Topología:** La topología de despliegue debe soportar el modelo arquitectónico definido (Monolito Modular, Microservicios, Serverless/Cloud Run, Agentes de IA, Event-Driven) y el runtime de ejecución especificado (Docker, Podman, Kubernetes, GCP Cloud Run, Bare Metal, etc.).
- **CONFIGURACIÓN DECLARATIVA Y SEGURA:** Cero credenciales, contraseñas o secretos en texto plano. Se exige el uso de perfiles de entorno (`dev`, `test`, `prod`) interpolados con gestores de secretos (GCP Secret Manager, HashiCorp Vault, Variables de Entorno del SO).
- **ESTRATEGIAS DE DEPLOYMENT:** La arquitectura debe considerar y detallar la estrategia de despliegue requerida (Canary, Blue-Green, Rolling Update, Recreate, Marcha Blanca) ajustada a la criticidad, SLA y tolerancia al fallo del proyecto.