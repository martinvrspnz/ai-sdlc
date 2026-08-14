# FASE 1: DISCOVERY Y REFINAMIENTO CONTEXTUAL

## 1. VISIÓN GENERAL Y OBJETIVO DE LA FASE
La Fase 1 transforma notas informales, audios, transcripciones y documentos heterogéneos en un **alcance conceptual estructurado, acotado y libre de ambigüedades**. Mediante entrevistas socráticas conducidas por la IA, se resuelven puntos ciegos, se define el Lenguaje Ubicuo (DDD) y se acota el MVP mediante la matriz MoSCoW.

---

## 2. ARQUITECTURA Y FLUJO DE TRABAJO DE FASE

```text
[ Notas / Audios / PDFs de Negocio ]
          │
          ▼
(Paso 0: NotebookLM) ──► Genera: Resumen Consolidado de Negocio
          │
          ▼
[ Orquestador de Fase 1: .prompts/system/phase/01-phase1-discovery.md ]
          │
  ┌───────┼──────────────────────────────┐
  ▼       ▼                              ▼
[Skill: Gap Analyzer]  [Skill: Socratic Interview]  [Skill: DDD Mapper]
  │       │                              │
  └───────┴──────────────┬───────────────┘
                         ▼
             (Comando: "GENERAR ARTEFACTOS")
                         │
                         ▼
             [ Artefactos: docs/01-discovery/ ]
```

---

## 3. ENTRADAS OBLIGATORIAS (INPUT CONTEXT)
- **Resumen Ejecutivo de Negocio:** Elaborado en NotebookLM mediante el prompt especializado a partir de las fuentes del cliente.
- **Guardrails Universales:** `.prompts/system/00-guardrails-base.md`.

---

## 4. ENTREGABLES Y ARTEFACTOS DE SALIDA (`docs/01-discovery/`)
Al ejecutar el comando de congelamiento (`"GENERAR ARTEFACTOS"`), se generan los 4 artefactos en la carpeta de destino:
1. `01-project-charter.md`: Definición del problema, propuesta de valor, KPIs cuantificables y fronteras del proyecto.
2. `02-ubiquitous-language.md`: Glosario oficial de términos canónicos y reglas de negocio bajo principios DDD.
3. `03-high-level-features.md`: Árbol de Épicas y Capacidades categorizadas bajo la técnica MoSCoW (`[FEAT-XX]`).
4. `04-gap-and-risk-analysis.md`: Matriz de brechas funcionales, clasificación de riesgos e itinerario de mitigación.

---

## 5. CRITERIOS DE ACEPTACIÓN DE LA FASE (GATE DE SALIDA)
La Fase 1 se concluye exitosamente cuando:
- [ ] Brechas críticas (`Gaps` de alto riesgo) aclaradas en las iteraciones socráticas.
- [ ] Alcance Must/Should/Won't Have validado sin sobrelapamiento de requerimientos.
- [ ] Los 4 artefactos en `docs/01-discovery/` aprobados por el usuario para pasar a la **Fase 2: Especificación Formalizada (SDD)**.