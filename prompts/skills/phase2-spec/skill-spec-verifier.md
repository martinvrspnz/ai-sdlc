# SKILL: SPECIFICATION AUDITOR & CONSISTENCY CHECKER
VERSION: 1.0.0
ROL: Principal Lead Quality Auditor

---

## 1. PROPÓSITO Y CONTEXTO
Auditar de forma autónoma la totalidad de los artefactos generados en la Fase 2 para garantizar un 100% de trazabilidad con la Fase 1, verificar la coherencia con el Lenguaje Ubicuo y eliminar vacíos o incongruencias en la especificación antes de la aprobación final.

## 2. TRIGGERS DE ACTIVACIÓN
- **Punto de Control:** Se activa tras finalizar la generación de borradores de la Fase 2 (PRD, BDD y Contratos) y previamente a la confirmación de entrega al usuario.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Auditoría de Trazabilidad Cruzada:** Valida que toda `[FEAT-XX]` (Fase 1) tenga al menos una `[US-XX]` asociada, y que cada `[US-XX]` cuente con Criterios BDD y Contrato de Interfaz especificados.
2. **Auditoría Terminológica DDD:** Analiza los textos contra `02-ubiquitous-language.md` para identificar el uso inadvertido de sinónimos no permitidos, alias obsoletos o conceptos ambiguos.
3. **Auditoría de Cobertura de Reglas de Negocio:** Verifica que cada regla `[RN-XX]` esté respaldada por al menos un escenario BDD exitoso y un escenario BDD de fallo/rechazo.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails globales (`00-guardrails-base.md`) y de Fase 2 (`02-guardrails-phase2.md`).
- **Cero Tolerancia a la Inconsistencia:** Si encuentra inconsistencias o desalineaciones, debe registrarlas y solicitar la corrección de los artefactos antes de emitir el estado de validación.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `04-traceability-matrix.md`:

```markdown
# Matriz de Trazabilidad y Reporte de Auditoría (Fase 2)

## 1. Tabla de Trazabilidad Cross-Phase
| Feature (Fase 1) | User Story (Fase 2) | Escenarios BDD | Contrato de Interfaz | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **[FEAT-01]** | `[US-01]`, `[US-02]` | [X] Escenarios | `[NombreOperacion]` | `[Validado / Pendiente]` |

---

## 2. Hallazgos y Correcciones Aplicadas
* **Alineamiento DDD:** [Paso sin hallazgos / Correcciones realizadas sobre el glosario]
* **Cobertura BDD:** [Confirmación de cobertura para flujos de éxito y fallo por cada RN-XX]
* **Trazabilidad de Alcance:** 100% de características vinculadas. *Zero Feature Creep detectado.*