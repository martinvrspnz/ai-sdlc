# SKILL: ADAPTER, CONTROLLER & MAPPER BUILDER
VERSION: 1.0.0
ROL: Infrastructure & Integration Software Engineer

---

## 1. PROPÓSITO Y CONTEXTO
Construir los adaptadores de entrada y salida (Controladores REST, Consumidores de Eventos, Repositorios de Persistencia y Clientes HTTP) conectando los puertos del dominio con la infraestructura física mediante Mappers que desacoplan los modelos de datos.

## 2. TRIGGERS DE ACTIVACIÓN
- **Integración de Capas:** Se activa para conectar los puertos del dominio desarrollados por `SKILL: DOMAIN & CORE USECASE BUILDER` con los componentes físicos especificados en el blueprint de la Fase 4[cite: 13, 15].

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Mapeo Explícito y Mappers Puros:** Implementa conversores declarativos o estáticos entre Entidades de Persistencia, Modelos de Dominio y DTOs de Contrato.
2. **Manejo Estándar de Errores:** Captura excepciones del dominio en la capa de adaptación y condúcelas a respuestas bajo el estándar **RFC 7807 (Problem Details)**.
3. **Inyección Segura de Configuración:** Inyecta credenciales y endpoints mediante variables de entorno y perfiles (`dev`, `prod`).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 5 (`05-guardrails-phase5.md`).
- **Zero DB-to-API Leak:** Prohibido retornar o filtrar Entidades de base de datos ORM directamente en las respuestas HTTP o adaptadores de entrada.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Los archivos creados se colocan en `/src/main/.../infrastructure/`:

```java
// Mapper de desacoplamiento (DB Entity <-> Domain <-> Contract DTO)  
public class AccountMapper {  
    public static AccountDomain toDomain(AccountEntity entity) {  
        return new AccountDomain(entity.getAccountNumber(), entity.getBalance());  
    }

    public static AccountResponseDTO toResponseDTO(AccountDomain domain) {  
        return new AccountResponseDTO(domain.accountNumber(), domain.balance());  
    }  
}

// Adaptador de Entrada (REST Controller)  
@Path("/api/v1/accounts")  
@Produces(MediaType.APPLICATION_JSON)  
@Consumes(MediaType.APPLICATION_JSON)  
public class AccountController {

    private final ProcessTransactionUseCasePort useCase;

    public AccountController(ProcessTransactionUseCasePort useCase) {  
        this.useCase = useCase;  
    }

    @POST  
    @Path("/withdraw")  
    public Response withdraw(@Valid WithdrawRequestDTO request) {  
        AccountDomain updatedAccount = useCase.execute(request.accountNumber(), request.amount());  
        return Response.ok(AccountMapper.toResponseDTO(updatedAccount)).build();  
    }  
}