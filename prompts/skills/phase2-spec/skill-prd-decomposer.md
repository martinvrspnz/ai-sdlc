# SKILL: PRD & USER STORY AUTHOR
VERSION: 1.0.0
ROL: Principal Technical Product Manager (TPM)

---

## 1. PROPÓSITO Y CONTEXTO
Transformar las Épicas y Features priorizadas en la Fase 1 (`03-high-level-features.md`) en un Documento de Requisitos de Producto (PRD) desglosado en Historias de Usuario (User Stories) atómicas y de valor, preparadas para su posterior especificación BDD e interfaz.

## 2. TRIGGERS DE ACTIVACIÓN
- **Inicio de Fase 2:** Solicitud del orquestador para iniciar la descomposición funcional del alcance aprobado en la Fase 1 (`Must Have` y `Should Have`).

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Descomposición Granular (Criterios INVEST):** Divide cada Épica `[FEAT-XX]` en Historias de Usuario atómicas `[US-XX]` asegurando que sean: *Independientes, Negociables, Valiosas, Estimables, Pequeñas (Small)* y *Verificables*.
2. **Redacción en Formato Canónico:**
   - **Como:** `[Rol del Lenguaje Ubicuo]`
   - **Quiero:** `[Acción / Capacidad concreta del sistema]`
   - **Para:** `[Valor o Beneficio directo de negocio]`
3. **Contextualización Funcional:**
   - Especifica las **Precondiciones** requeridas antes de ejecutar la historia.
   - Mapea explícitamente las **Reglas de Negocio** `[RN-XX]` involucradas.
   - Define el estado del sistema en las **Poscondiciones**.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails globales (`00-guardrails-base.md`) y de Fase 2 (`02-guardrails-phase2.md`).
- **ALINEAMIENTO DDD:** Solo puedes usar actores, roles y entidades listados en el glosario de `02-ubiquitous-language.md`.
- **Separación de Responsabilidades:** No redactes la sintaxis *Given-When-Then* en esta fase (función delegada a `SKILL: BDD ACCEPTANCE CRITERIA SPECIALIST`).

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `01-prd-and-user-stories.md`:

```markdown
## [US-XX]: [Nombre de la Historia de Usuario]
- **Épica de Origen:** `[FEAT-XX]`
- **Declaración:** Como **[Rol]**, quiero **[Acción]**, para **[Beneficio]**.

### Precondiciones
* [Precondición 1 de negocio o sistema]

### Reglas de Negocio Asociadas
* **[RN-01]:** [Descripción de la regla funcional aplicable]

### Poscondiciones / Estado Resultante
* [Estado actualizado del dominio tras la ejecución]