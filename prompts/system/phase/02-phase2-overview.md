# FASE 2: ESPECIFICACIÓN FORMALIZADA (SPEC-DRIVEN DEVELOPMENT - SDD)

## 1. VISIÓN GENERAL Y OBJETIVO DE LA FASE
La Fase 2 transforma el alcance conceptual de la Fase 1 en **especificaciones técnicas y funcionales ejecutables y deterministas**. Se desglosan las Épicas en Historias de Usuario INVEST, se construyen criterios BDD en Gherkin y se diseñan contratos lógicos de interfaz desacoplados de detalles de infraestructura o bases de datos.

---

## 2. ARQUITECTURA Y FLUJO DE TRABAJO DE FASE

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                       INPUTS (Fase 1 - Discovery)                       │
│  • 01-project-charter.md        • 02-ubiquitous-language.md             │
│  • 03-high-level-features.md    • 04-gap-and-risk-analysis.md           │
└─────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
[ Orquestador Fase 2: .prompts/system/phase/02-phase2-specification.md ]
                                     │
  ┌──────────────────────────────────┼─────────────────────────────────┐
  ▼                                  ▼                                 ▼
[Skill: PRD Author]       [Skill: BDD Specialist]    [Skill: Contract Designer]
  │                                  │                                 │
  └──────────────────────────┬───────┴─────────────────────────────────┘
                             ▼
             [Skill: Specification Verifier]
                             │
            (Comando: "GENERAR ESPECIFICACIONES")
                             │
                             ▼
             [ Artefactos: docs/02-specification/ ]
```

---

## 3. ENTRADAS OBLIGATORIAS (INPUT CONTEXT)
- **Artefactos de Fase 1:** Documentos presentes en `docs/01-discovery/`.
- **Guardrails Aplicables:**
  - `.prompts/system/00-guardrails-base.md`
  - `.prompts/system/02-guardrails-phase2.md`

---

## 4. ENTREGABLES Y ARTEFACTOS DE SALIDA (`docs/02-specification/`)
Tras ejecutar `"GENERAR ESPECIFICACIONES"`, se emiten 4 archivos Markdown:
1. `01-prd-and-user-stories.md`: PRD detallado con Historias de Usuario `[US-XX]`, Precondiciones y Reglas `[RN-XX]`.
2. `02-bdd-acceptance-criteria.md`: BDDs deterministas redactados bajo sintaxis Given-When-Then.
3. `03-api-and-data-contracts.md`: Especificación lógica de DTOs, campos obligatorios, validaciones y modelos de error RFC 7807.
4. `04-traceability-matrix.md`: Matriz de trazabilidad Requisito -> US -> BDD -> Contrato y reporte de consistencia.

---

## 5. CRITERIOS DE ACEPTACIÓN DE LA FASE (GATE DE SALIDA)
La Fase 2 concluye cuando:
- [ ] Cobertura del 100% de las características Must/Should por Historias de Usuario y escenarios BDD.
- [ ] Escenarios BDD con flujos principales, alternativos y de fallo deterministas.
- [ ] Cero Feature Creep y cumplimiento total del Lenguaje Ubicuo.
- [ ] Aprobación de los 4 artefactos en `docs/02-specification/` para dar paso a la **Fase 3: Skill Factory**.