# **AI-SDLC: Marco de Desarrollo de Software Potenciado por IA**

Este repositorio contiene la especificación operacional, la arquitectura metodológica y la guía de ejecución del ciclo de vida de desarrollo de software asistido por Inteligencia Artificial (**AI-SDLC**).

El marco combina **Spec-Driven Development (SDD)**, **Skill-Driven Development (SkDD)**, **Domain-Driven Design (DDD)** y **Test-Driven Development (TDD)** adaptándose a cualquier stack tecnológico, arquitectura y modelo de infraestructura.

## **🏗️ 1\. Arquitectura del Proceso AI-SDLC**

El ciclo de desarrollo se compone de 7 fases estructuradas para minimizar alucinaciones y maximizar la precisión técnica y la calidad de código:

\[Insumos Brutos / Idea\]  
       │  
       ▼  
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐  
│  FASE 1:     │ ──► │  FASE 2:     │ ──► │  FASE 3:     │ ──► │  FASE 4:     │  
│  Discovery y │     │  Especif.    │     │  Skills y    │     │  Arquitectura│  
│  Refinamiento│     │  (SDD)       │     │  Agentes     │     │  y Diseño    │  
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘  
                                                                     │  
┌──────────────┐     ┌──────────────┐     ┌──────────────┐           │  
│  FASE 7:     │ ◄── │  FASE 6:     │ ◄── │  FASE 5:     │ ◄─────────┘  
│  Mantenimien.│     │  Despliegue  │     │  Construcción│  
│  y Mejora    │     │  y Ops       │     │  y Pruebas   │  
└──────────────┘     └──────────────┘     └──────────────┘

## **📁 2\. Estructura del Repositorio (Prompt Engineering as Code)**

Toda la inteligencia del sistema, guardrails y habilidades especializadas de cada fase están empaquetadas y versionadas en archivos Markdown dentro del proyecto:

mi-proyecto/  
├── README.md                                    \# Guía principal del marco AI-SDLC  
├── .cursorrules                                 \# Reglas de entorno auto-generadas en Fase 3  
├── .prompts/  
│   ├── system/  
│   │   ├── guardrails/  
│   │   │   ├── 00-guardrails-base.md            \# Guardrails globales universales  
│   │   │   ├── 02-guardrails-phase2.md          \# Guardrails de la Fase 2 (SDD & RNF)  
│   │   │   ├── 03-guardrails-phase3.md          \# Guardrails de la Fase 3 (Meta-Skill Factory)  
│   │   │   ├── 04-guardrails-phase4.md          \# Guardrails de la Fase 4 (Arquitectura & RNF)  
│   │   │   └── 05-guardrails-phase5.md          \# Guardrails de la Fase 5 (TDD / SkDD & RNF)  
│   │   ├── 01-phase1-discovery.md               \# Orquestador principal de la Fase 1  
│   │   ├── 02-phase2-specification.md          \# Orquestador principal de la Fase 2  
│   │   ├── 03-phase3-skill-factory.md           \# Orquestador Meta-Skill Factory (Fase 3\)  
│   │   ├── 04-phase4-architecture.md            \# Orquestador principal de la Fase 4  
│   │   └── 05-phase5-construction.md            \# Orquestador principal de la Fase 5  
│   ├── notebooklm/  
│   │   ├── 01-notebooklm-summary.md             \# Prompt para ingesta de idea/brief (Fase 1\)  
│   │   └── 02-notebooklm-tech-stack-summary.md \# Prompt para ingesta técnica (Fase 3\)  
│   └── skills/  
│       ├── phase1/  
│       │   ├── skill-gap-analyzer.md            \# Skill: Análisis de brechas y riesgos  
│       │   ├── skill-socratic-interviewer.md     \# Skill: Entrevista socrática (Max 3 preguntas)  
│       │   ├── skill-ddd-domain-mapper.md        \# Skill: Extracción de Lenguaje Ubicuo (DDD)  
│       │   └── skill-moscow-prioritizer.md       \# Skill: Clasificación MoSCoW y MVP  
│       ├── phase2/  
│       │   ├── skill-prd-decomposer.md          \# Skill: Descomposición PRD e Historias (INVEST)  
│       │   ├── skill-bdd-gherkin-author.md      \# Skill: Criterios BDD deterministas (Gherkin)  
│       │   ├── skill-interface-contract-designer.md \# Skill: Contratos Funcionales de Interfaz  
│       │   └── skill-spec-verifier.md           \# Skill: Auditoría de consistencia y trazabilidad  
│       ├── phase3/                              \# SKILLS GENERADOS DINÁMICAMENTE EN FASE 3  
│       │   └── skill-custom-\[tecnologia\].md  
│       ├── phase4/  
│       │   ├── skill-c4-architecture-designer.md       \# Skill: C4 Model, Patrones y Mappers  
│       │   ├── skill-db-data-modeler.md                \# Skill: Modelado de Persistencia Multi-paradigma  
│       │   ├── skill-testing-strategy-architect.md     \# Skill: Estrategia de Pruebas Multi-capa  
│       │   └── skill-infrastructure-deploy-architect.md \# Skill: Topología, Contenedores, Deployment y Scaffolding  
│       └── phase5/  
│           ├── skill-tdd-test-builder.md            \# Skill: Pruebas automatizadas TDD y BDD (Fase RED)  
│           ├── skill-domain-usecase-builder.md      \# Skill: Núcleo de Dominio, Reglas y Puertos (Fase GREEN)  
│           ├── skill-adapter-controller-builder.md  \# Skill: Adaptadores, Controladores y Mappers (Fase GREEN)  
│           └── skill-code-quality-refactoring.md    \# Skill: Clean Code, Observabilidad y RNF (Fase REFACTOR)  
├── src/                                         \# CÓDIGO FUENTE PRODUCTIVO Y PRUEBAS  
│   ├── main/                                    \# Dominio, Casos de Uso, Mappers y Adaptadores  
│   └── test/                                    \# Suites de Pruebas Unitarias e Integración BDD  
└── docs/  
    ├── 01-discovery/                            \# Artefactos finales de la Fase 1  
    │   ├── 00-phase1-overview.md  
    │   ├── 01-project-charter.md  
    │   ├── 02-ubiquitous-language.md  
    │   ├── 03-high-level-features.md  
    │   └── 04-gap-and-risk-analysis.md  
    ├── 02-specification/                        \# Artefactos finales de la Fase 2 (SDD)  
    │   ├── 00-phase2-overview.md  
    │   ├── 01-prd-and-user-stories.md  
    │   ├── 02-bdd-acceptance-criteria.md  
    │   ├── 03-api-and-data-contracts.md  
    │   └── 04-traceability-matrix.md  
    ├── 03-skills-and-agents/                    \# Insumos y catálogo de la Fase 3 (SkDD)  
    │   ├── 00-phase3-overview.md  
    │   └── tech-stack-definition.md  
    ├── 04-architecture/                         \# Artefactos finales de la Fase 4  
    │   ├── 00-phase4-overview.md  
    │   ├── 01-software-architecture.md  
    │   ├── 02-data-model-and-persistence.md  
    │   ├── 03-testing-strategy.md  
    │   ├── 04-infrastructure-and-deploy.md  
    │   └── 05-project-scaffolding-guide.md  
    └── 05-construction/                         \# Artefactos finales de la Fase 5 (TDD / SkDD)  
        ├── 00-phase5-overview.md  
        ├── 01-implementation-report.md  
        ├── 02-test-execution-report.md  
        └── 03-nfr-validation-report.md

## **🛡️ 3\. Guardrails del Proyecto**

### **Guardrails Base Universales (.prompts/system/guardrails/00-guardrails-base.md)**

1. **Restricción de Stack:** Adherencia estricta a las tecnologías aprobadas para la solución.  
2. **Anti-Alucinación y Manejo de Gaps:** Prohibido asumir reglas de negocio ambiguas; deben marcarse como GAP.  
3. **Privacidad de Datos:** Cero credenciales, claves API o datos de carácter personal (PII).  
4. **Neutralidad Temática:** Exclusión estricta de debates políticos, religiosos, bélicos o discriminatorios.  
5. **Lenguaje Profesional:** Prohibición total de vulgaridades, sarcasmo o groserías locales.  
6. **Intervención Humana (HITL):** Aprobación explícita del usuario requerida para congelar cada fase.

### **Guardrails Específicos de la Fase 2 (.prompts/system/guardrails/02-guardrails-phase2.md)**

1. **Alineamiento con Lenguaje Ubicuo:** Uso estricto de los términos del glosario 02-ubiquitous-language.md.  
2. **Sintaxis BDD Determinista:** Criterios de aceptación en formato Gherkin (*Given-When-Then*) libres de ambigüedades.  
3. **Abstracción Técnica de Contratos:** Definición del *Qué* (contratos funcionales) sin acoplar detalles de infraestructura o DDL físico.  
4. **Captura Explícita de RNF:** Requerimientos No Funcionales (latencia, seguridad, observabilidad) documentados formalmente por Historia de Usuario.  
5. **Zero Feature Creep:** Trazabilidad estricta contra las características aprobadas en la Fase 1\.

### **Guardrails Específicos de la Fase 3 (.prompts/system/guardrails/03-guardrails-phase3.md)**

1. **Alineamiento con el Tech Stack:** Los skills autogenerados deben basarse exclusivamente en la definición técnica aprobada (tech-stack-definition.md).  
2. **Atomicidad y Enfoque Único:** Principio de Lean Skill (un único patrón o responsabilidad técnica por archivo).  
3. **Seguridad y Parámetros Interpolados:** Cero credenciales quemadas (*hardcoded*); uso de inyección segura y Secret Managers.  
4. **Estructura Estándar Markdown:** Cumplimiento riguroso de las 6 secciones estándar de un Skill SkDD.

### **Guardrails Específicos de la Fase 4 (.prompts/system/guardrails/04-guardrails-phase4.md)**

1. **Alineamiento Absoluto al Stack:** Decisiones derivadas estrictamente de tech-stack-definition.md.  
2. **Modelado C4 & Mermaid Standard:** Diagramas C4 (Contexto, Contenedores, Componentes) y modelos de datos redactados exclusivamente en Mermaid.  
3. **Desacoplamiento Estricto (Hexagonal / Clean Architecture):** El dominio permanece aislado de frameworks y persistencia; uso obligatorio de Mappers (Zero DB-to-API leak).  
4. **Modelado de Persistencia Multi-paradigma:** Soporte para SQL, NoSQL, Parquet, Archivos Planos, Key-Value, etc., con versionado de esquemas.  
5. **Diseño Arquitectónico y Validación de RNF:** Incorporación de patrones de resiliencia, observabilidad y Quality Gates para métricas RNF.  
6. **Estrategia de Testing Integral:** Pruebas multi-capa (Unitarias, Integración, Carga/Estrés, Humo y Marcha Blanca).  
7. **Infraestructura y Despliegue Declarativo:** Configuración por entornos, interpolación de secretos y estrategias de despliegue (Canary, Blue-Green, Rolling Update, Marcha Blanca).

### **Guardrails Específicos de la Fase 5 (.prompts/system/guardrails/05-guardrails-phase5.md)**

1. **Ciclo TDD Estricto (RED \-\> GREEN \-\> REFACTOR):** Desarrollo guiado por pruebas donde la suite automatizada se escribe antes que el código productivo.  
2. **Adherencia Rigurosa al Blueprint y Contratos:** Organización estricta por paquetes, aislamiento del dominio y desacoplamiento obligatorio vía Mappers (Zero DB-to-API leak).  
3. **Verificación Automatizada de RNF:** Instrumentación de observabilidad (Trace IDs, logs estructurados sin PII) y validación de límites de latencia y seguridad OWASP.  
4. **Protección de Alcance (Lean Code / YAGNI):** Cero código innecesario o abstracciones no solicitadas fuera de las Historias de Usuario \[US-XX\].  
5. **Pass Rate 100% Obligatorio:** Cero módulos finalizados con pruebas fallidas o ignoradas.

## **🛠️ 4\. Guía de Ejecución Paso a Paso**

### **Requisitos Previos**

* Cuenta en [NotebookLM](https://notebooklm.google.com/)  
* Acceso a [Google AI Studio](https://aistudio.google.com/) o IDE con agente de IA (Cursor, VSCode, Cline)  
* Repositorio Git con la estructura .prompts/ configurada

### **FASE 1: Discovery y Refinamiento**

#### **Paso 1: Ingesta y Sintetización en NotebookLM**

1. Ingresa a **NotebookLM** y crea un cuaderno para el proyecto.  
2. Carga los materiales brutos disponibles (notas de voz, PDFs, transcripciones, notas sueltas).  
3. Ejecuta el prompt .prompts/notebooklm/01-notebooklm-summary.md.  
4. Copia el resumen estructurado resultante.

#### **Paso 2: Sesión Socrática en Google AI Studio / IDE**

1. Vincula en **System Instructions**:  
   * .prompts/system/guardrails/00-guardrails-base.md  
   * .prompts/system/01-phase1-discovery.md  
   * Skills de .prompts/skills/phase1/  
2. Pega el resumen de NotebookLM en el chat.  
3. Responde a las rondas de preguntas socráticas (máximo 3 por turno).

#### **Paso 3: Congelamiento de Fase 1**

1. Envía el comando: GENERAR ARTEFACTOS.  
2. Guarda los archivos resultantes en /docs/01-discovery/.

### **FASE 2: Especificación Formalizada (Spec-Driven Development \- SDD)**

#### **Paso 1: Configuración de Contexto**

1. Configura en las instrucciones del sistema:  
   * Guardrails base y de Fase 2 (.prompts/system/guardrails/00-guardrails-base.md, .prompts/system/guardrails/02-guardrails-phase2.md)  
   * Orquestador .prompts/system/02-phase2-specification.md  
   * Skills de .prompts/skills/phase2/

#### **Paso 2: Ingesta de Contexto de Fase 1**

1. Carga como entrada la carpeta /docs/01-discovery/.  
2. Inicia el proceso de descomposición funcional y captura de RNF.

#### **Paso 3: Generación y Congelamiento**

1. La IA invocará los skills de Fase 2 (skill-prd-decomposer.md, skill-bdd-gherkin-author.md, skill-interface-contract-designer.md, skill-spec-verifier.md).  
2. Al finalizar la revisión, envía el comando: GENERAR ESPECIFICACIONES.  
3. Guarda los archivos resultantes en /docs/02-specification/.

### **FASE 3: Skill Factory y Configuración de Agentes (SkDD)**

#### **Paso 0: Ingesta Tecnológica en NotebookLM**

1. Crea un cuaderno en **NotebookLM** e ingiere los documentos técnicos del stack.  
2. Ejecuta .prompts/notebooklm/02-notebooklm-tech-stack-summary.md.  
3. Guarda el resultado en /docs/03-skills-and-agents/tech-stack-definition.md.

#### **Paso 1: Ejecución de la Meta-Skill Factory**

1. Configura en el sistema:  
   * Todos los guardrails de .prompts/system/guardrails/\*.md  
   * Orquestador .prompts/system/03-phase3-skill-factory.md  
2. Carga como contexto las carpetas /docs/02-specification/ y /docs/03-skills-and-agents/.

#### **Paso 2: Generación de Skills Técnicos y Configuración de Entorno**

1. La Meta-Skill Factory propondrá la lista exacta de Skills técnicos requeridos.  
2. Envía el comando: GENERAR SKILLS.  
3. Guarda los archivos .md resultantes en .prompts/skills/phase3/ y la configuración de entorno (.cursorrules).

### **FASE 4: Arquitectura, Modelado e Infraestructura**

#### **Paso 1: Configuración del Entorno de Fase 4**

1. Configura en las instrucciones del agente o sistema:  
   * Guardrails de .prompts/system/guardrails/\*.md (incluyendo 04-guardrails-phase4.md)  
   * Orquestador .prompts/system/04-phase4-architecture.md  
   * Skills de .prompts/skills/phase4/

#### **Paso 2: Ingesta de Especificaciones y Stack Técnico**

1. Carga como contexto de entrada:  
   * /docs/02-specification/\*.md  
   * /docs/03-skills-and-agents/\*.md  
   * /.prompts/skills/phase3/\*.md

#### **Paso 3: Elaboración de Blueprints Técnicos**

1. El orquestador invocará en secuencia los 4 skills de la fase:  
   * skill-c4-architecture-designer.md: Diagramación C4 en Mermaid, desacoplamiento y Mappers.  
   * skill-db-data-modeler.md: Modelo de datos (SQL, NoSQL, Parquet, etc.), ER y migraciones.  
   * skill-testing-strategy-architect.md: Estrategia de pruebas multi-capa y Quality Gates RNF.  
   * skill-infrastructure-deploy-architect.md: Topología, contenedores, secretos por entorno, estrategias de deployment y scaffolding.

#### **Paso 4: Congelamiento de Fase 4**

1. Tras revisar el blueprint técnico con el usuario, envía el comando: GENERAR ARTEFACTOS.  
2. Guarda los 5 archivos resultantes en la carpeta /docs/04-architecture/.

### **FASE 5: Construcción, Codificación y Pruebas (TDD / SkDD)**

#### **Paso 1: Configuración del Entorno de Construcción**

1. Configura en el agente de codificación:  
   * Guardrails de .prompts/system/guardrails/\*.md (incluyendo 05-guardrails-phase5.md)  
   * Orquestador .prompts/system/05-phase5-construction.md  
   * Skills de .prompts/skills/phase5/, .prompts/skills/phase3/ y .prompts/skills/phase4/

#### **Paso 2: Ingesta de Especificaciones y Arquitectura**

1. Carga como fuentes de verdad estrictas:  
   * /docs/02-specification/\*.md  
   * /docs/04-architecture/\*.md

#### **Paso 3: Ejecución del Ciclo TDD (Red \-\> Green \-\> Refactor)**

1. **Fase RED:** Invocación de skill-tdd-test-builder.md para escribir las pruebas unitarias e integración en /src/test/... mapeando los escenarios BDD de la Fase 2\.  
2. **Fase GREEN:** Invocación de skill-domain-usecase-builder.md y skill-adapter-controller-builder.md para escribir el código mínimo suficiente en /src/main/... hasta hacer pasar todos los tests.  
3. **Fase REFACTOR:** Invocación de skill-code-quality-refactoring.md para optimizar legibilidad (Clean Code), instrumentar observabilidad y certificar RNF.

#### **Paso 4: Certificación y Reportes de Cierre**

1. Tras validar que el Pass Rate es 100%, envía el comando: GENERAR REPORTES FASE 5\.  
2. Guarda el código fuente en /src/ y los reportes resultantes en /docs/05-construction/.
