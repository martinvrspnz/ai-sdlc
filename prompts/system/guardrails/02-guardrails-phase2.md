# GUARDRAILS ESPECÍFICOS - FASE 2: ESPECIFICACIÓN FORMALIZADA (SDD)
VERSION: 2.0.0
APLICACIÓN: Fase 2 (Requerimientos, Documento PRD, Historias de Usuario, Criterios BDD y Contratos de Interfaz)
PREVALENCIA: Se aplica en adición y cumplimiento estricto a las reglas base definidas en `.prompts/system/00-guardrails-base.md`.

---

## 1. ALINEAMIENTO DELIMITADO Y DELIMITACIÓN DE FASE
- **Enfoque Exclusivo de Fase 2:** Esta fase se limita estricta y exclusivamente a la especificación funcional y no funcional formalizada (Documentos PRD, Historias de Usuario, Criterios de Aceptación BDD y Contratos Lógicos de Interfaz).
- **Prohibición de Fases Posteriores:** Queda estrictamente prohibido en esta fase escribir código fuente de producción en Java (Fase 5), redactar scripts DDL SQL reales para bases de datos (Fase 4), generar diagramas C4 formales (Fase 4) o diseñar archivos de despliegue Dockerfile/Kubernetes (Fase 4).

## 2. ALINEAMIENTO ESTRICTO CON EL LENGUAJE UBICUO (DDD NAMING ENFORCEMENT)
- **Glosario Canónico:** Todos los nombres de actores, entidades, atributos, eventos, objetos de valor y acciones descritos en las Historias de Usuario, escenarios BDD o Contratos de Interfaz DEBEN utilizar ÚNICAMENTE la terminología oficial registrada en el artefacto `docs/01-discovery/02-ubiquitous-language.md`.
- **Prohibición de Sinónimos:** Queda estrictamente prohibido introducir sinónimos, alias no aprobados, traducciones arbitrarias (ej. alternar entre inglés y español sin control) o nuevos términos de negocio sin haber actualizado e incorporado explícitamente dichos términos en el glosario de la Fase 1.

## 3. BDD DETERMINISTA Y SINTAXIS GHERKIN VERIFICABLE
- **Sintaxis Estricta:** Los Criterios de Aceptación deben redactarse obligatoriamente siguiendo la sintaxis Gherkin estándar: `Dado [Contexto] / Cuando [Acción] / Entonces [Resultado]` (`Given-When-Then`).
- **Prohibición de Ambigüedad:** Queda PROHIBIDO el uso de afirmaciones vagas, ambiguas, subjetivas o cualitativas (ej. "el sistema debe responder rápido", "se muestra un mensaje amigable", "el sistema funciona bien" o "se maneja el error adecuadamente").
- **Determinismo Operativo:** Cada escenario debe especificar de forma cuantitativa e inequívoca la condición inicial exacta, el estímulo/acción concreta del actor y el resultado esperado determinista (ej. especificando nombres exactos de campos retornados, cambios explícitos de estado en la entidad, o el código e identificador de error de negocio emitido).

## 4. ABSTRACCIÓN TÉCNICA DE CONTRATOS (ESPECIFICACIÓN VS. ARQUITECTURA)
- **Definición del QUÉ:** Los contratos de interfaz definen EL QUÉ (datos de entrada requeridos y opcionales, tipos de datos lógicos, validaciones de dominio, reglas de negocio asociadas y respuestas de error conceptuales).
- **Aislamiento Físico:** No deben imponer detalles de implementación física de infraestructura, frameworks o base de datos (ej. no incluir tipos de datos SQL específicos como `VARCHAR(255)`, sentencias DDL, anotaciones de ORM/Panache o frameworks de serialización). Esto se delega exclusivamente a la Fase 4 (Arquitectura).
- **Adaptabilidad según Paradigma:** El diseño debe adaptarse con la misma rigurosidad según la arquitectura objetivo especificada:
  * **Monolito Multimódulo:** Interfaces de dominio Java / DTOs lógicos de transferencia entre paquetes.
  * **Agente de IA:** Schemas de entrada/salida para declaración de Tools / Function Calling (parámetros y descripciones).
  * **API REST / Eventos:** Payloads JSON conceptuales, verbos lógicos y códigos de estado HTTP/Eventos.

## 5. ESPECIFICACIÓN OBLIGATORIA DE REQUERIMIENTOS NO FUNCIONALES (RNF)
- **Sección RNF Obligatoria:** Cada Historia de Usuario `[US-XX]` y el Documento PRD deben incluir obligatoriamente una sección explícita de Requerimientos No Funcionales (RNF) con métricas cuantificables y verificables.
- **Categorías Mínimas Requeridas:**
  * **Rendimiento / Latencia:** Tiempo máximo de respuesta permitido expresado en percentiles P95/P99 (ej. Latencia < 200ms en P95).
  * **Concurrencia / Throughput:** Carga y capacidad esperada expresada en métricas claras (ej. TPS objetivo o número de usuarios concurrentes).
  * **Seguridad / Privacidad:** Niveles de autenticación, esquema de encriptación y clasificación explícita de datos PII.
  * **Observabilidad / Auditoría:** Contextos de traza requeridos (ej. Trace ID) y eventos de negocio obligatorios para auditoría.

## 6. TRAZABILIDAD Y PROTECCIÓN DE ALCANCE (ZERO FEATURE CREEP)
- **Vinculación 1:1:** Cada Historia de Usuario `[US-XX]`, Escenario BDD y Contrato de Interfaz debe vincularse directamente a una Épica o Feature `[FEAT-XX]` previamente registrada en `docs/01-discovery/03-high-level-features.md`.
- **Cero Feature Creep:** No se permite bajo ninguna circunstancia agregar nuevas funcionalidades, reglas no contempladas, campos extra o módulos adicionales durante la especificación sin un ticket de cambio aprobado que modifique primero los artefactos de la Fase 1.