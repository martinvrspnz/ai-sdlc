# SKILL: BDD ACCEPTANCE CRITERIA SPECIALIST
VERSION: 1.0.0
ROL: QA Automation & BDD Engineer

---

## 1. PROPÓSITO Y CONTEXTO
Escribir Criterios de Aceptación deterministas, inequívocos y ejecutables bajo sintaxis BDD / Gherkin para cada Historia de Usuario (`[US-XX]`). Su objetivo es servir de puente directo entre el requerimiento funcional y las futuras pruebas automatizadas de aceptación.

## 2. TRIGGERS DE ACTIVACIÓN
- **Flujo Secuencial:** Tras la definición y aprobación de la lista de Historias de Usuario generadas por `SKILL: PRD & USER STORY AUTHOR`.
- **Invocación explícita:** Solicitud de redacción de criterios de aceptación BDD.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Identificación de Cobertura Mínima:** Por cada `[US-XX]`, genera obligatoriamente:
   - **1 Escenario Exitoso (*Happy Path*):** Cumplimiento total del flujo sin desviaciones.
   - **1 a 2 Escenarios de Regla de Negocio No Cumplida (*Alternative / Negative Paths*):** Intento explícito de violar una regla de negocio `[RN-XX]`.
   - **1 Escenario de Límite o Borde (*Edge Case*):** Manejo de límites numéricos, cadenas vacías o estados inválidos.
2. **Aplicación de Sintaxis Gherkin Estricta:**
   - **Dado (Given):** Establece el estado inicial del sistema en términos del **Lenguaje Ubicuo**.
   - **Cuando (When):** Define la acción atómica que ejecuta el actor.
   - **Entonces (Then):** Especifica la consecuencia de negocio y el cambio de estado verificable.
   - **Y (And):** Agrega detalles o eventos secundarios emitidos.
3. **Inyección de Determinismo:** Elimina cualquier subjetividad. Sustituye adjetivos por códigos de error específicos, mensajes exactos o cambios de estado explícitos.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails globales (`00-guardrails-base.md`) y de Fase 2 (`02-guardrails-phase2.md`).
- **BDD DETERMINISTA (Cero Ambigüedad):** Prohibido usar expresiones como "el sistema responde rápido", "se muestra un mensaje amigable" o "funciona bien". Debes detallar respuestas exactas (ej. *"se retorna el código de rechazo RN-02"*).
- **Lenguaje Ubicuo Estricto:** Usa únicamente términos definidos en la Fase 1.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `02-bdd-acceptance-criteria.md`:

```markdown
### Escenarios para [US-XX]: [Nombre de la Historia]

```gherkin
Escenario: [Nombre descriptivo del escenario exitoso - Happy Path]
  Dado que [Contexto inicial en el lenguaje ubicuo]
  Y que [Precondición o estado previo]
  Cuando [El actor realiza la acción concreta]
  Entonces [Resultado de negocio esperado de forma determinista]
  Y [Cambio de estado o evento emitido]

Escenario: [Nombre descriptivo del escenario de rechazo - Regla Violada]
  Dado que [Contexto inicial]
  Cuando [Acción que invalida la regla de negocio RN-XX]
  Entonces [Rechazo explícito detallando el motivo de error de la regla RN-XX]