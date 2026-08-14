# GUARDRAILS ESPECÍFICOS - FASE 3: SKILL FACTORY Y AGENTES DE TRABAJO (SkDD)
VERSION: 2.0.0
APLICACIÓN: Fase 3 (Meta-Generación de Skills Técnicos, Prompts e Instrucciones de Agentes de Trabajo)
PREVALENCIA: Se aplica de forma obligatoria durante la Meta-Generación de Skills Técnicos y la configuración de agentes en la Fase 3, en adición a los guardrails universales (`.prompts/system/00-guardrails-base.md`) y de fases anteriores.

---

## 1. ALINEAMIENTO DELIMITADO Y DELIMITACIÓN DE FASE
- **Enfoque Exclusivo de Fase 3:** Esta fase se aboca EXCLUSIVAMENTE a la creación, estandarización, meta-generación y optimización de prompts de Skills técnicos y configuraciones de comportamiento de agentes de trabajo.
- **Prohibición de Fases Posteriores:** Queda estrictamente prohibido en esta fase construir el blueprint final de la arquitectura (Fase 4), modelar bases de datos físicas (Fase 4) o redactar las clases y archivos de código fuente Java de producción (Fase 5).

## 2. DETERMINISMO Y FORMATO ESTÁNDAR DE SKILLS
- **Ubicación y Formato:** Todo Skill técnico generado dinámicamente debe ser un archivo Markdown (`.md`) completamente autocontenido en la carpeta `.prompts/skills/phase3/`.
- **Secciones Obligatorias:** Debe cumplir estrictamente con las 6 secciones estándar estructuradas:
  1. *Propósito y Contexto*
  2. *Trigger de Activación*
  3. *Estándares y Convenciones Aplicadas (Metodología)*
  4. *Patrón de Código de Referencia (Snippet ejecutable)*
  5. *Guardrails Locales y Restricciones*
  6. *Output Esperado (Output Schema)*.
- **Cero Generacidad:** Queda estrictamente PROHIBIDO generar Skills genéricos que no tengan un snippet de código o configuración ejecutable basada directamente en el stack técnico oficial del proyecto.

## 3. ALINEAMIENTO CON EL STACK TÉCNICO OFICIAL
- **Aherencia Total a la Síntesis Técnica:** Ningún Skill generado puede sugerir, incluir o utilizar librerías, dependencias, versiones o frameworks que contradigan la síntesis técnica definida en `/docs/03-skills-and-agents/tech-stack-definition.md`.
- **Especialización Quarkus:** Si el stack define Java LTS con Quarkus Reactivo (Mutiny) y Hibernate Reactive / Panache, todos los Skills de persistencia y API deben basarse EXCLUSIVAMENTE en esos componentes. Queda prohibido incluir ejemplos imperativos si se especificó un enfoque reactivo.

## 4. SEGURIDAD Y DESARROLLO SEGURO POR DISEÑO (SEC-BY-DESIGN)
- **Patrones de Seguridad en Snippets:** Todo Snippet de código incluido como patrón de referencia dentro de un Skill debe implementar patrones de seguridad por defecto:
  * **Inyección Segura:** Inyección segura de parámetros y consultas preparadas (prevención explícita de vulnerabilidades de SQL/NoSQL Injection y vulnerabilidades tipo Log4j / Code Injection).
  * **Manejo Seguro de Secretos:** Manejo de secretos exclusivamente mediante SmallRye Config / GCP Secret Manager. Queda estrictamente prohibido hardcodear credenciales, URLs de base de datos, contraseñas o tokens en los snippets de referencia.
  * **Sanitización de Entradas:** Sanitización implícita y validación de atributos de entrada en los contratos REST / DTOs mediante anotaciones de Bean Validation (`@Valid`, `@NotNull`, `@Size`).

## 5. TRATAMIENTO DE ERRORES Y MANEJO DE EXCEPCIONES UNIFICADO
- **Estándar RFC 7807:** Los Skills que generen código de interfaz, controladores o servicios deben incluir explícitamente el patrón de captura de excepciones y mapeo unificado hacia respuestas funcionales estructuradas bajo el estándar **RFC 7807 (Problem Details)**.
- **Prohibición de Manejo Silencioso:** Prohibido generar snippets que utilicen bloques `catch (Exception e)` silenciosos, vacíos o que retornen trazas internas de error (`StackTrace`) al usuario final o cliente de la API.

## 6. PRINCIPIO DE RESPONSABILIDAD ÚNICA DE SKILL (LEAN SKILLS)
- **Atomicidad de Capacidades:** Cada Skill debe resolver UNA SOLA capacidad técnica o tarea del desarrollo (ej. "Skill de Persistencia Panache", "Skill de Endpoint REST Reactivo", "Skill de Integración GCP Secret Manager").
- **Prohibición Monolítica:** Prohibido crear Skills monolíticos o sobrecargados que intenten abarcar arquitectura, bases de datos, lógica de negocio y despliegue dentro de un solo archivo de instrucción.