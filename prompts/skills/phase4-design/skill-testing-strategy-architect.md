# SKILL: MULTI-LAYER TESTING STRATEGY ARCHITECT
VERSION: 1.0.0
ROL: Principal QA Architect & Test Strategist

---

## 1. PROPÓSITO Y CONTEXTO
Definir la estrategia integral de pruebas de software abarcando todas las capas de la pirámide/diamante de pruebas (Unitarias, Integración, Carga/Estrés, Humo y Marcha Blanca/Stage). Establece los Quality Gates de cobertura de código, métricas SLA de performance y trazabilidad estricta contra la Fase 2.

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase 4:** Activación para la elaboración del artefacto `03-testing-strategy.md`.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Definición de Capas Obligatorias:**
   - **Pruebas Unitarias:** Cobertura de lógica de dominio pura mediante aislado con Test Doubles.
   - **Pruebas de Integración y Contrato:** Validación de persistencia, comunicaciones inter-módulo y escenarios BDD usando contenedores temporales o emuladores.
   - **Pruebas de Carga y Estrés:** Definición de escenarios de volumen evaluando latencias (ej. P95) y rendimiento bajo métricas SLA.
   - **Pruebas de Humo (Smoke Tests):** Verificación post-despliegue mediante verificaciones rápidas de estado de salud.
   - **Marcha Blanca / Stage:** Pruebas E2E en entornos réplica con datos anonimizados.
2. **Mapeo BDD a Pruebas de Integración:** Asigna obligatoriamente cada escenario Gherkin definido en `02-bdd-acceptance-criteria.md` a un test de integración o contrato.
3. **Establecimiento de Quality Gates:** Define umbrales mínimos de aprobación (*Pass Rates*) y porcentaje de cobertura para el pipeline de CI/CD.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 4 (`04-guardrails-phase4.md`).
- **Mapeo BDD Obligatorio:** Todo escenario BDD escrito en la Fase 2 debe figurar explícitamente dentro de la suite de integración o contrato. No se admiten criterios BDD sin prueba asociada.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `03-testing-strategy.md`:

```markdown
# Estrategia Integral de Pruebas y Quality Gates

## 1. Matriz General de Pruebas

| Tipo de Prueba | Cobertura / Objetivo | Herramientas Recomendadas | Criterio de Aceptación (Pass Rate) |
| :--- | :--- | :--- | :--- |
| **Unitarias** | Lógica de Dominio, Reglas de Negocio | According to Stack (JUnit / PyTest / Jest) | `>= 80%` Cobertura de Líneas |
| **Integración / Contrato** | Contratos DTO, API, Persistencia | Testcontainers / WireMock / Memory DB | `100%` Escenarios BDD Fase 2 |
| **Carga y Estrés** | Latencia P95 < 200ms, Throughput SLA | k6 / JMeter / Locust | `0%` Tasa de Error bajo carga nominal |
| **Humo (Smoke Test)** | Endpoints de Salud (`/health`, `/ready`) | cURL / Postman CLI | `100%` Exitoso post-despliegue |
| **Marcha Blanca** | Flujos E2E en Staging | Framework E2E / Manuales Guiadas | Aprobación Criterios de Aceptación |

---

## 2. Mapeo de Escenarios BDD a Pruebas de Integración
* **`[US-01]` - Escenario Exitoso:** Mapeado a `TransactionServiceIntegrationTest#shouldProcessSuccessfully()`.
* **`[US-01]` - Escenario Regla Violada `[RN-01]`:** Mapeado a `TransactionServiceIntegrationTest#shouldRejectInvalidRule()`.