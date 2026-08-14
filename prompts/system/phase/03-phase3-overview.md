# FASE 3: SKILL FACTORY Y CONFIGURACIÓN DE AGENTES (SkDD)

## 1. VISIÓN GENERAL Y OBJETIVO DE LA FASE
La Fase 3 opera como una **Fábrica de Habilidades Técnicas (Meta-Skill Factory)**. En esta etapa no se programa la solución final, sino que se analiza la especificación de la Fase 2 y la definición del stack tecnológico para **auto-generar la librería de Skills Técnicos (.md)** que orquestarán las fases de arquitectura, desarrollo y pruebas.

---

## 2. ARQUITECTURA Y FLUJO DE TRABAJO DE FASE

```text
[ Manuales, Guías y Normas Técnicas ]
                 │
                 ▼
(Paso 0: NotebookLM) ──► Genera: tech-stack-definition.md
                 │
┌────────────────┴─────────────────────────────────────────────┐
│                                                              │
│  [ docs/02-specification/*.md ] + [ docs/03-skills-and-agents/*.md ]│
│  (PRD, BDD, Contratos)            (Síntesis del Stack Técnico)       │
└────────────────┬─────────────────────────────────────────────┘
                 │
                 ▼
[ Meta-Skill Factory: .prompts/system/phase/03-phase3-skill-factory.md ]
                 │
                 ▼
[ Librería de Skills Técnicos: .prompts/skills/phase3/*.md ]
```

---

## 3. ENTRADAS OBLIGATORIAS (INPUT CONTEXT)
1. **Especificación Funcional (Fase 2):** Archivos en `docs/02-specification/`.
2. **Definición del Stack Técnico:** `docs/03-skills-and-agents/tech-stack-definition.md`.
3. **Guardrails Aplicables:**
   - `.prompts/system/00-guardrails-base.md`
   - `.prompts/system/03-guardrails-phase3.md`[cite: 24, 31]

---

## 4. ENTREGABLES Y ARTEFACTOS DE SALIDA
- **Librería de Skills Técnicos en `.prompts/skills/phase3/`:** Prompts autocontenidos para persistencia, controladores, integraciones GCP, patrones reactivos y pruebas.
- **Gobernanza y Reglas de Contexto:** Instrucciones de soporte para IDEs (`.cursorrules`) y agentes de desarrollo.

---

## 5. CRITERIOS DE ACEPTACIÓN DE LA FASE (GATE DE SALIDA)
La Fase 3 se completa cuando:
- [ ] Archivo `tech-stack-definition.md` consolidado en `docs/03-skills-and-agents/`.
- [ ] Todos los Skills auto-generados en `.prompts/skills/phase3/` cumplen con los guardrails de fase.
- [ ] Colección aprobada para iniciar la **Fase 4: Arquitectura, Modelado e Infraestructura**.