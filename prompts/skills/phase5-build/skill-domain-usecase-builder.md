# SKILL: DOMAIN & CORE USECASE BUILDER
VERSION: 1.0.0
ROL: Domain-Driven Design (DDD) Core Developer

---

## 1. PROPÓSITO Y CONTEXTO
Construir el núcleo del negocio (entidades, agregados, objetos de valor y reglas de negocio) e interfaces/puertos (Ports) en la capa interna de la arquitectura (Hexagonal/Clean/Onion). Su objetivo es lograr el estado **GREEN** en la fase TDD asegurando aislamiento total de la infraestructura tecnológica.

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase GREEN TDD:** Se activa tras confirmar el fallo (fase RED) de las pruebas de unidad presentadas por `SKILL: TDD & BDD TEST BUILDER`.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Inmutabilidad por Diseño:** Define agregados, entidades y Objetos de Valor (*Value Objects*) utilizando estructuras inmutables (ej. *Java Records*, *Data Classes* en Kotlin/Python).
2. **Modelo de Dominio Rico (*Rich Domain Model*):** Embebe las validaciones de las reglas de negocio `[RN-XX]` directamente en las entidades de dominio para evitar modelos anémicos.
3. **Inversión de Dependencias (Interfaces/Puertos):** Expón únicamente interfaces de entrada (*Input Ports / Use Cases*) y salidas (*Output Ports / Repositories*).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 5 (`05-guardrails-phase5.md`).
- **Aislamiento Tecnológico Absoluto:** Prohibido importar librerías de persistencia (JPA, Hibernate, Panache), serialización (Jackson) o frameworks web (JAX-RS, Spring Web) en la capa de dominio.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Los archivos generados se ubican en `/src/main/.../domain/`:

```java
// Entidad de Dominio Inmutable con validación de regla de negocio
public record AccountDomain(String accountNumber, BigDecimal balance) {  
    public AccountDomain {  
        if (balance == null || balance.compareTo(BigDecimal.ZERO) < 0) {  
            throw new BusinessException("El balance inicial no puede ser negativo");  
        }  
    }

    public AccountDomain withdraw(BigDecimal amount) {  
        if (amount.compareTo(this.balance) > 0) {  
            throw new InsufficientFundsException("Fondos insuficientes para el retiro");  
        }  
        return new AccountDomain(this.accountNumber, this.balance.subtract(amount));  
    }  
}

// Puerto de Salida (Output Port)  
public interface AccountRepositoryPort {  
    Optional<AccountDomain> findByNumber(String accountNumber);  
    void save(AccountDomain account);  
}