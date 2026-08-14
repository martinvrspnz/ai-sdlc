# SKILL: INTERFACE & DATA CONTRACT SPECIFIER
VERSION: 1.0.0
ROL: API & Integration Software Architect

---

## 1. PROPÓSITO Y CONTEXTO
Especificar los Contratos Funcionales de Interfaz y Estructura de Datos (DTOs lógicos, entradas, salidas y modelos de error) necesarios para dar soporte a las Historias de Usuario, desacoplando la definición lógica del patrón arquitectónico final.

## 2. TRIGGERS DE ACTIVACIÓN
- **Flujo Secuencial:** Se activa automáticamente tras la especificación de escenarios BDD para una Historia de Usuario `[US-XX]`.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Análisis del Intercambio de Información:** Analiza las Historias de Usuario y sus escenarios BDD para derivar los datos mínimos requeridos de entrada y salida.
2. **Abstracción por Patrón de Arquitectura:** Adapta la representación lógica al paradigma aplicable del proyecto:
   - *Monolito Multimódulo (ej. Quarkus):* Contrato de interfaz Java de dominio / DTO entre paquetes.
   - *Sistemas Basados en Agentes IA:* Schema de *Tool / Function Calling* (parámetros de entrada, descripciones e intenciones).
   - *API REST / Event-Driven:* Payload JSON conceptual, verbos lógicos (Crear/Consultar/Actualizar) o estructura de evento emitido.
3. **Estructuración de Atributos:**
   - Define el nombre del campo siguiendo la convención del dominio.
   - Determina el tipo de dato lógico (*Texto, Entero, Booleano, UUID, Fecha, Enum*).
   - Especifica la obligatoriedad y las reglas de validación asignadas (`[RN-XX]`).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails globales (`00-guardrails-base.md`) y de Fase 2 (`02-guardrails-phase2.md`).
- **ABSTRACCIÓN TÉCNICA:** Prohibido incluir sentencias DDL SQL, anotaciones de frameworks (ej. Hibernate, Jackson, Spring), o detalles de infraestructura física. La especificación debe mantenerse a nivel conceptual y de contrato lógico.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `03-api-and-data-contracts.md`:

```markdown
### Contrato de Interfaz para [US-XX]
- **Nombre de Interfaz / Operación:** `[NombreConceptualOperacion]`
- **Tipo de Interacción:** `[Inter-módulo Java / Tool de Agente / API REST / Evento]`

#### Datos de Entrada (Input Payload / DTO)
| Campo | Tipo Lógico | Requerido | Validación / Regla de Negocio |
| :--- | :--- | :--- | :--- |
| `[nombreCampo]` | `[Texto / UUID / etc.]` | `[Sí / No]` | Debe cumplir con la regla `[RN-XX]` / Formato X |

#### Datos de Salida (Output Payload)
| Campo | Tipo Lógico | Descripción |
| :--- | :--- | :--- |
| `[nombreCampo]` | `[Identificador / Enum]` | [Descripción lógica de la respuesta emitida] |

#### Respuestas de Error Funcionales
| Código / Identificador Error | Condición de Desencadenamiento | Estructura de Respuesta |
| :--- | :--- | :--- |
| `[ERR-RN-XX]` | Intento de procesar datos sin cumplir `[RN-XX]` | `{ "error": "[Código]", "mensaje": "[Causa]" }` |