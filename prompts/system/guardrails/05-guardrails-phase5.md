# GUARDRAILS ESPECÍFICOS - FASE 5: CONSTRUCCIÓN, CODIFICACIÓN Y PRUEBAS (TDD / SkDD)
VERSION: 2.0.0
APLICACIÓN: Fase 5 (Generación de Código Fuente Java, Creación de Suites de Pruebas Automatizadas y Refactorización Clean Code)
PREVALENCIA: Estos guardrails se aplican de forma obligatoria durante la generación de código fuente, creación de suites de pruebas y refactorización en la Fase 5. Complementan a los guardrails base (`00-guardrails-base.md`) y a las definiciones aprobadas en las Fases 2, 3 y 4.

---

## 1. CICLO TDD ESTRICTO (RED -> GREEN -> REFACTOR)
- **PRIMERO LAS PRUEBAS (Fase RED):** Ninguna línea de código productivo de casos de uso, servicios, agregados o adaptadores debe escribirse sin que exista previamente una prueba automatizada que falle demostrando su necesidad y justificando su creación.
- **PRUEBAS DERIVADAS DE BDD:** Toda prueba de integración o contrato debe correlacionarse 1:1 con los escenarios BDD redactados en sintaxis Gherkin de la Fase 2 (`docs/02-specification/02-bdd-acceptance-criteria.md`).
- **CÓDIGO MÍNIMO SUFICIENTE (Fase GREEN):** Escribe únicamente la lógica de producción estrictamente necesaria para hacer pasar la prueba en ejecución. Prohibido agregar código extra o anticipar escenarios no probados.
- **REFACTORIZACIÓN SEGURA (Fase REFACTOR):** Aplica mejoras de legibilidad, optimización y patrones Clean Code/SOLID solo y únicamente cuando la suite completa de pruebas se encuentre en verde (100% Pass Rate).

## 2. ADHERENCIA RIGUROSA AL BLUEPRINT DE ARQUITECTURA Y CONTRATOS
- **Cumplimiento de Estructura:** El código fuente construido debe respetar al 100% la estructura de paquetes, patrones (Hexagonal, Clean Architecture, Onion) y decisiones de diseño definidas en el blueprint de `/docs/04-architecture/`.
- **AISLAMIENTO DEL DOMINIO:** Las clases, agregados, entidades de negocio y reglas del núcleo (`/domain/`) no deben bajo ninguna circunstancia importar paquetes de infraestructura, controladores, frameworks web (JAX-RS, Spring Web) o librerías de persistencia (JPA, Hibernate, Panache).
- **DESACOPLAMIENTO OBLIGATORIO:** Está estrictamente PROHIBIDO retornar entidades de persistencia en los controladores o adaptadores de interfaz. Toda transformación debe pasar obligatoriamente por la capa de Mappers especificada en el blueprint de arquitectura.

## 3. VERIFICACIÓN Y PRUEBAS DE REQUERIMIENTOS NO FUNCIONALES (RNF)
- **Instrumentación de Observabilidad:** El código fuente construido debe instrumentar activamente la observabilidad (OpenTelemetry, trazas distribuidas con Trace ID / Transaction ID, métricas de rendimiento y logs estructurados sin datos PII).
- **Validación de SLAs:** Durante la construcción y refactorización, es obligatorio validar mediante pruebas de integración, benchmarks o suites de carga que el módulo cumple con los **SLA/RNF** especificados en la Fase 2 y Fase 4 (latencia P95, consumo eficiente de memoria/CPU, manejo correcto de concurrencia y límites de payload).

## 4. PROTECCIÓN DE ALCANCE Y LEAN CODE (ZERO FEATURE CREEP)
- **Codificación Acotada:** Solo se codificarán los endpoints, métodos, campos, DTOs y reglas de negocio descritos explícitamente en las Historias de Usuario `[US-XX]` y Contratos Funcionales de la Fase 2.
- **Principio YAGNI (You Aren't Gonna Need It):** Queda prohibido agregar funcionalidades "futuras", métodos utilitarios no requeridos actualmente, parámetros opcionales no especificados o abstracciones innecesarias que incrementen la complejidad del código.

## 5. SEGURIDAD EN CÓDIGO, MANEJO DE EXCEPCIONES Y OBSERVABILIDAD
- **SEGURIDAD POR DISEÑO:** Inyección segura de dependencias y parámetros, prevención explícita de vulnerabilidades OWASP Top 10 (SQL/NoSQL Injection, XSS, Path Traversal, Command Injection).
- **CERO CREDENCIALES EN CÓDIGO:** Queda prohibido hardcodear contraseñas, tokens, claves secretas, API keys o URLs de entorno en clases Java o archivos de código fuente. Todo debe inyectarse dinámicamente desde variables de entorno o gestores de secretos (GCP Secret Manager / SmallRye Config).
- **MANEJO UNIFICADO DE ERRORES:** Captura de excepciones traducida obligatoriamente al formato estándar de respuestas de error o RFC 7807 (Problem Details) definido en los contratos de la Fase 2.
- **LOGGING Y TRAZABILIDAD:** Inclusión de registros estructurados (logs) con contexto de correlación (Trace ID / Transaction ID) sin exponer en ningún momento datos sensibles ni información PII (Personally Identifiable Information).

## 6. VERIFICACIÓN AUTOMATIZADA Y CRITERIO DE COMPLETITUD (PASS RATE 100%)
- **Cero Tolerancia a Fallos:** Ningún módulo, clase o componente se considerará finalizado si presenta pruebas automatizadas en estado fallido (`Failed`), con errores o ignoradas (`@Disabled`, `@Ignore`).
- **Pass Rate 100% Obligatorio:** La suite de pruebas unitarias y de integración debe ejecutarse y validar una tasa de éxito del 100% (Pass Rate) en los escenarios de prueba antes de dar paso al reporte de implementación o entrega del componente.