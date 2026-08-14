# PROMPT DE SÍNTESIS Y ESTÁNDAR TÉCNICO PARA NOTEBOOKLM (TECH STACK INPUT)
VERSION: 2.0.0
APLICACIÓN: Entrada técnica en NotebookLM para la Fase 3 (Meta-Skill Factory)
PROCESO DESTINO: Generación de `docs/03-skills-and-agents/tech-stack-definition.md` e insumo para `.prompts/system/phase/03-phase3-skill-factory.md`

---

## 1. OBJETIVO Y PROPÓSITO
Analizar minuciosamente todas las fuentes técnicas cargadas en este cuaderno de NotebookLM (manuales oficiales de frameworks, guías de arquitectura internas, especificaciones de GCP, ejemplos de código de referencia, políticas de desarrollo seguro) para sintetizar la **Definición Técnica Unificada del Stack** que servirá de insumo directo para la generación automática de Skills de desarrollo.

## 2. INSTRUCCIONES DE EJECUCIÓN
Consolida los parámetros técnicos de las fuentes en una especificación estructurada respetando el estándar oficial de arquitectura (Java LTS + Quarkus + GCP).

## 3. GUARDRAILS TÉCNICOS, ÉTICA Y SEGURIDAD
- **Tono Estrictamente Técnico:** Mantén un tono 100% técnico, objetivo, estructurado, riguroso y profesional.
- **Alineamiento al Stack del Proyecto:** Basa la síntesis EXCLUSIVAMENTE en la documentación cargada. No asumas tecnologías no mencionadas salvo que se deriven del stack oficial (Java LTS, Quarkus, Google Cloud Platform). Queda prohibido proponer o incluir alternativas de Spring Boot, Node.js, AWS o Azure.
- **Desarrollo Seguro:** Exige el cumplimiento de reglas OWASP Top 10, sanitización de datos, inyección segura de parámetros y cero credenciales hardcodeadas.
- **Filtro de Tono y Contenido:** Prohibido incluir opiniones personales, comentarios fuera de contexto, lenguaje agresivo, vulgaridades o jerga Soez.

---

## 4. ESTRUCTURA Y FORMATO DE SALIDA REQUERIDO

Consolida la síntesis técnica aplicando exactamente la siguiente plantilla en Markdown:

```markdown
# Definición Oficial del Stack Tecnológico del Proyecto

## 1. LENGUAJE Y RUNTIME
* **Versión del Lenguaje:** Java LTS (versión exacta especificada en los manuales).
* **Características Permitidas y Estándares:** Features del lenguaje autorizadas (ej. Records para DTOs/Inmutabilidad, Pattern Matching, Sealed Classes, Switch Expressions).
* **Prácticas Desaconsejadas:** Construcciones o librerías restringidas en el código fuente.

---

## 2. FRAMEWORK PRINCIPAL Y EXTENSIONES
* **Versión del Framework:** Quarkus (versión exacta detectada).
* **Paradigma de Ejecución:** Modelo de ejecución reactivo (Mutiny / SmallRye) o imperativo según los lineamientos internos.
* **Extensiones Habilitadas:** Lista de extensiones Quarkus a utilizar (ej. RESTEasy Reactive, Hibernate ORM con Panache / Reactive, SmallRye OpenAPI, Quarkus Security, Quarkus SmallRye Config).

---

## 3. NUBE E INFRAESTRUCTURA (GCP)
* **Servicios de Google Cloud Platform:** Lista de componentes GCP seleccionados (ej. GCP Secret Manager, Cloud Run, Cloud Storage, Pub/Sub, Cloud SQL, Cloud Logging).
* **Gestión de Configuración y Secretos:** Estrategia de interpolación utilizando SmallRye Config con GCP Secret Manager y perfiles por entorno (`dev`, `test`, `prod`).

---

## 4. PATRONES DE ARQUITECTURA Y ESTRUCTURA DE CÓDIGO
* **Estilo Arquitectónico:** Patrón de diseño del sistema (Arquitectura Hexagonal / Ports & Adapters, Clean Architecture, Monolito Modular).
* **Organización de Paquetes:** Convención de empaquetado (Package by Feature / Package by Layer).
* **Convenciones de Nomenclatura:** Estándares de naming para Clases, Interfaces, DTOs, Entidades Panache, Puertos y Repositorios.
* **Manejo Global de Excepciones:** Patrón de captura de errores y mapeo hacia el estándar RFC 7807 (Problem Details).

---

## 5. ESTRATEGIA DE TESTING Y CALIDAD
* **Frameworks de Prueba:** Bibliotecas autorizadas (JUnit 5, RestAssured, QuarkusTest).
* **Mocks e Integración:** Estrategias de aislamiento y contenedores para pruebas de integración (Testcontainers, WireMock, Dev Services).
* **Quality Gates:** Umbral mínimo de cobertura de código esperado (ej. >= 80% en dominio/aplicación).

---

## 6. SEGURIDAD Y NORMATIVAS TÉCNICAS
* **Mecanismos de Autenticación / Autorización:** Estándares de seguridad (JWT, OIDC, OAuth2, RBAC con roles Quarkus Security).
* **Desarrollo Seguro:** Medidas de protección OWASP Top 10, sanitización de datos de entrada y prevención explícita de inyecciones (SQL, Command, Log).

---

## 7. GAPS Y OMISIONES TÉCNICAS DETECTADAS
* Lista explícita de decisiones de arquitectura, dependencias, versiones o librerías que NO están especificadas en los materiales cargados y que requieren una definición prioritaria por el Arquitecto de Software.