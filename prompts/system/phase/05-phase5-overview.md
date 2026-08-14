# FASE 5: CONSTRUCCIÓN, CODIFICACIÓN Y PRUEBAS (TDD / SkDD)

## 1. VISIÓN GENERAL Y OBJETIVO DE LA FASE
La Fase 5 ejecuta la construcción del software ejecutable aplicando **Test-Driven Development (TDD)** y **Skill-Driven Development (SkDD)**. Los agentes de desarrollo toman los contratos BDD (Fase 2), la librería de Skills técnicos (Fase 3) y el Blueprint de Arquitectura (Fase 4) para codificar la solución mediante el ciclo estricto *Red -> Green -> Refactor*.

---

## 2. ARQUITECTURA Y FLUJO DE TRABAJO DE FASE

```text
┌──────────────────────────────────────────────────────────────────────────────┐
│                           INPUTS OBLIGATORIOS                                │
│  • docs/02-specification/*.md (PRD, BDD, Contratos, Matriz RNF)             │
│  • docs/04-architecture/*.md (C4 Model, Data Model, Test Strategy, IaC)     │
│  • .prompts/skills/phase3/*.md (Librería de Skills Técnicos)                 │
└──────────────────────────────────────────────────────────────────────────────┘
                                   │
                                   ▼
[ Orquestador de Construcción: .prompts/system/phase/05-phase5-construction.md ]
                                   │
  ┌──────────────────────┬─────────┴────────────┬──────────────────────────┐
  ▼                      ▼                      ▼                          ▼
[Skill: TDD Tests]   [Skill: Domain/Core]  [Skill: Adapt/Ctrl]   [Skill: Clean Code]
  └──────────────────────┴─────────┬────────────┴──────────────────────────┘
                                   │
                                   ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                         CÓDIGO Y ENTREGABLES                                 │
│  • Código Fuente (`src/main/...`) y Suites de Test (`src/test/...`)          │
│  • docs/05-construction/01-implementation-report.md                          │
│  • docs/05-construction/02-test-execution-report.md                          │
│  • docs/05-construction/03-nfr-validation-report.md                          │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. ENTRADAS OBLIGATORIAS (INPUT CONTEXT)
1. **Especificación Funcional (Fase 2):** Criterios BDD, Contratos y RNF en `docs/02-specification/`.
2. **Blueprint de Arquitectura (Fase 4):** Diagramas C4, Modelo de Persistencia y Estrategia de Pruebas en `docs/04-architecture/`.
3. **Librería de Skills Técnicos (Fase 3):** Prompts especializados en `.prompts/skills/phase3/`.
4. **Guardrails Aplicables:**
   - `.prompts/system/00-guardrails-base.md`
   - `.prompts/system/05-guardrails-phase5.md`

---

## 4. ENTREGABLES Y ARTEFACTOS DE SALIDA
- **Código Fuente y Tests (`src/`):** Clases Java en `src/main/...` y suites de prueba en `src/test/...`.
- **Artefactos en `docs/05-construction/`:**
  - `00-phase5-overview.md`: Documento de gobernanza y visión general de la fase.
  - `01-implementation-report.md`: Mapeo de componentes desarrollados contra Historias `[US-XX]`.
  - `02-test-execution-report.md`: Reporte de ejecución con un Pass Rate del 100% y métricas de cobertura.
  - `03-nfr-validation-report.md`: Certificación formal de latencias P95, resiliencia y seguridad OWASP.

---

## 5. CRITERIOS DE ACEPTACIÓN DE LA FASE (GATE DE SALIDA)
La Fase 5 concluye cuando:
- [ ] Suite de pruebas con un Pass Rate del 100% (0 tests fallidos o ignorados).
- [ ] Cada escenario BDD de la Fase 2 respaldado por al menos un test ejecutable.
- [ ] Cero fugas de modelos de persistencia directamente en las interfaces de API.
- [ ] Los 3 reportes en `docs/05-construction/` aprobados para pasar a la **Fase 6: Despliegue, QA y Operaciones**.