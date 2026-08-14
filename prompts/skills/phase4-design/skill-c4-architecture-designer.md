# SKILL: C4 ARCHITECTURE & SOFTWARE DESIGN SPECIALIST
VERSION: 1.0.0
ROL: Principal Software Architect

---

## 1. PROPÓSITO Y CONTEXTO
Diseñar el blueprint de arquitectura de software utilizando el modelo C4 (Contexto, Contenedores, Componentes) en sintaxis Mermaid. Define el patrón arquitectónico objetivo (Hexagonal / Clean Architecture / DDD) y especifica los mecanismos de desacoplamiento estricto entre capas para aislar el dominio de la tecnología.

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase 4:** Activación para la elaboración del artefacto `01-software-architecture.md`.
- **Invocación explícita:** Solicitud de diagramación C4 o diseño de desacoplamiento de capas.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Adopción del Patrón Arquitectónico:** Consulta la definición técnica de `/docs/03-skills-and-agents/tech-stack-definition.md` para aplicar Hexagonal (Ports & Adapters), Clean Architecture o DDD.
2. **Diagramación C4 Cierre de Bucle:**
   - **Nivel 1 (Contexto):** Identifica actores, sistemas principales y sistemas externos.
   - **Nivel 2 (Contenedores):** Define aplicaciones, APIs, microservicios, agentes de IA, bases de datos y buses de eventos.
   - **Nivel 3 (Componentes):** Detalla los módulos internos (Capas de Dominio, Aplicación e Infraestructura).
3. **Mapeo de Trazabilidad:** Incluye en cada diagrama una leyenda funcional con la vinculación explícita a las Historias de Usuario `[US-XX]` de la Fase 2.
4. **Diseño de Desacoplamiento (Zero-Leak Pattern):** Especifica las interfaces (Puertos) y la estrategia de mapeo explícito (Mappers/DTOs) entre la persistencia/API y las entidades del dominio.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 4 (`04-guardrails-phase4.md`).
- **Zero DB-to-API Leak:** Queda estrictamente prohibido exponer entidades de base de datos o frameworks ORM directamente en las interfaces de entrada/salida o contratos DTO.
- Todos los diagramas C4 deben ser exclusivamente renderizables en sintaxis `mermaid` nativa.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `01-software-architecture.md`:

```markdown
# Blueprint de Arquitectura de Software

## 1. Diagramas C4 (Sintaxis Mermaid)

### Nivel 1: Diagrama de Contexto
```mermaid
C4Context
  title Diagrama de Contexto del Sistema (C4 Nivel 1)
  Person(user, "Usuario / Rol", "Actor principal del dominio")
  System(system, "Sistema Core", "Procesa lógica de negocio e integraciones")
  System_Ext(extSystem, "Sistema Externo", "Proveedor de servicios / API externa")

  Rel(user, system, "Interactúa mediante", "HTTPS/UI")
  Rel(system, extSystem, "Invocación de servicio", "mTLS/JSON")