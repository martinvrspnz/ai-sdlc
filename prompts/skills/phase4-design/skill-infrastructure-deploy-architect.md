# SKILL: INFRASTRUCTURE, DEPLOYMENT & SCAFFOLDING ARCHITECT
VERSION: 1.0.0
ROL: Principal DevOps & Infrastructure Architect

---

## 1. PROPÓSITO Y CONTEXTO
Diseñar la topología de infraestructura, containerización en entornos productivos, gestión declarativa de secretos, estrategias de despliegue sin interrupciones (Blue-Green, Canary, Rolling Update) y la arquitectura física de directorios/scaffolding del repositorio.

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase 4:** Activación para la creación de los artefactos `04-infrastructure-and-deploy.md` y `05-project-scaffolding-guide.md`.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Diseño de Containerización Multi-Stage:** Redacta `Dockerfile` o `Containerfile` optimizados separando las etapas de compilación (*build*) y ejecución (*runtime*).
2. **Estrategia de Despliegue y Secretos:**
   - Define el mecanismo de despliegue (Canary, Blue-Green, Rolling Update).
   - Configura la inyección de secretos declarativa vinculando variables de entorno a perfiles (`dev`, `test`, `prod`) sin exponer credenciales.
3. **Estructura del Repositorio (Scaffolding):** Construye el árbol físico de directorios del proyecto asegurando coherencia con el patrón arquitectónico (ej. capas de dominio, aplicación e infraestructura).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 4 (`04-guardrails-phase4.md`).
- **Cero Secretos Hardcodeados:** Prohibido incluir contraseñas, tokens o claves en archivos de código o diagramas. Toda referencia productiva debe apuntar a interpolación mediante Gestor de Secretos (Vault, AWS Secrets Manager, GCP Secret Manager, Kubernetes Secrets).

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Resultado listo para incorporar en `04-infrastructure-and-deploy.md` y `05-project-scaffolding-guide.md`:

```markdown
# Especificación de Infraestructura, Despliegue y Scaffolding

## 1. Containerización Multi-Stage (`Dockerfile`)

```dockerfile
# Stage 1: Build
FROM maven:3.9-eclipse-temurin-21 AS builder
WORKDIR /workspace
COPY pom.xml .
COPY src src
RUN mvn clean package -DskipTests

# Stage 2: Runtime
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /workspace/target/*.jar app.jar
USER 1001
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]


├── .prompts/                     # Framework de Prompts y Skills
├── docs/                         # Documentación as Code (Fases 1 a 6)
├── src/
│   ├── main/
│   │   ├── java/com/empresa/app/
│   │   │   ├── domain/           # Entidades, Reglas de Negocio y Puertos
│   │   │   ├── application/      # Casos de Uso y DTOs
│   │   │   └── infrastructure/   # Controladores, Repositorios y Adaptadores
│   │   └── resources/            # Configuración por perfil (application.yml)
│   └── test/                     # Pruebas Unitarias e Integración
├── Dockerfile
└── pom.xml