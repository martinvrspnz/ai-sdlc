# FASE 4: ARQUITECTURA, MODELADO E INFRAESTRUCTURA

## 1. VISIÓN GENERAL Y OBJETIVO DE LA FASE
La Fase 4 traduce las especificaciones funcionales (Fase 2) y la definición técnica (Fase 3) en el **Blueprint Técnico de la Solución**. En esta etapa se construye la arquitectura C4 Model, se especifica la persistencia multi-paradigma, se establece la estrategia de pruebas multi-capa y se diseña la infraestructura y el despliegue en GCP.

---

## 2. ARQUITECTURA Y FLUJO DE TRABAJO DE FASE

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                           INPUTS OBLIGATORIOS                           │
│  • docs/02-specification/*.md (PRD, BDD, Contratos, Trazabilidad)       │
│  • docs/03-skills-and-agents/*.md (Stack Técnico, Overview)             │
│  • .prompts/skills/phase3/*.md (Librería de Skills Técnicos)            │
└─────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
[ Orquestador de Arquitectura: .prompts/system/phase/04-phase4-architecture.md ]
                                     │
  ┌───────────────────────┬──────────┴───────────┬──────────────────────┐
  ▼                       ▼                      ▼                      ▼
[Skill: C4 Designer] [Skill: Data Model] [Skill: Test Strategy] [Skill: Infrastructure]
  └───────────────────────┴──────────┬───────────┴──────────────────────┘
                                     │
                                     ▼
                  [ OUTPUTS: docs/04-architecture/ ]
                  • 01-software-architecture.md
                  • 02-data-model-and-persistence.md
                  • 03-testing-strategy.md
                  • 04-infrastructure-and-deploy.md
                  • 05-project-scaffolding-guide.md
```

---

## 3. ENTRADAS OBLIGATORIAS (INPUT CONTEXT)
1. **Especificación Funcional:** Artefactos en `docs/02-specification/`.
2. **Stack Técnico y Skills:** Archivo `tech-stack-definition.md` y librería en `.prompts/skills/phase3/`.
3. **Guardrails Aplicables:**
   - `.prompts/system/00-guardrails-base.md`
   - `.prompts/system/04-guardrails-phase4.md`[cite: 25, 34]

---

## 4. ENTREGABLES Y ARTEFACTOS DE SALIDA (`docs/04-architecture/`)
1. `01-software-architecture.md`: Modelo C4 (Mermaid), patrón hexagonal y Mappers.
2. `02-data-model-and-persistence.md`: Modelo físico de datos (Mermaid ER), migración e índices.
3. `03-testing-strategy.md`: Estrategia de pruebas multi-capa y Quality Gates.
4. `04-infrastructure-and-deploy.md`: Dockerfiles multi-stage, perfiles y GCP Secret Manager.
5. `05-project-scaffolding-guide.md`: Guía de scaffolding y estructura de archivos base.

---

## 5. CRITERIOS DE ACEPTACIÓN DE LA FASE (GATE DE SALIDA)
La Fase 4 concluye cuando:
- [ ] Todos los diagramas renderizan correctamente en Mermaid.
- [ ] Mappers implementados para desacoplar el dominio y evitar la fuga de entidades ORM.
- [ ] Los 5 artefactos en `docs/04-architecture/` aprobados para iniciar la **Fase 5: Construcción y Codificación (TDD/SkDD)**.