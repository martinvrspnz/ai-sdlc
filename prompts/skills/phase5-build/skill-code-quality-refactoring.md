# SKILL: CODE QUALITY, REFACTORING & NFR VALIDATOR
VERSION: 1.0.0
ROL: Lead Quality & Observability Engineer (Clean Code Auditor)

---

## 1. PROPÓSITO Y CONTEXTO
Ejecutar la fase **REFACTOR** del ciclo TDD. Optimiza la legibilidad del código, aplica principios Clean Code/SOLID, e instrumenta la observabilidad, sanitización de datos (OWASP) y el cumplimiento de Requerimientos No Funcionales (RNF).

## 2. TRIGGERS DE ACTIVACIÓN
- **Fase REFACTOR TDD:** Se activa una vez que toda la suite de pruebas unitarias e integrales se encuentra en verde (**GREEN**) y antes de marcar un componente como completado.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Refactorización Clean Code & SOLID:** Elimina código duplicado (DRY), reduce la complejidad ciclomática y simplifica métodos extensos.
2. **Instrumentación de Observabilidad:** Agrega registros (logs) estructurados enriquecidos con identificadores de correlación (*Trace ID / Transaction ID*).
3. **Validación RNF y Sanitización Security:**
   - Sanitiza datos de entrada para prevenir inyecciones (OWASP).
   - Aplica técnicas de *hashing* o enmascaramiento para asegurar que datos sensibles (PII) no se registren en los logs.

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 5 (`05-guardrails-phase5.md`).
- **Preservación del Pass Rate:** Toda refactorización debe mantener el 100% de pruebas pasando. Si alguna prueba se rompe, la refactorización debe revertirse.
- Prohibido modificar contratos de interfaz o alterar los RNF acordados en la Fase 4.

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Código refactorizado depositado en `/src/main/...` y reporte de calidad para consolidación en `/docs/05-construction/`:

```java
// Método refactorizado con observabilidad, hashing PII y sanitización
public AccountDomain executeWithdrawal(String accountNumber, BigDecimal amount) {  
    String sanitizedAccount = SanitizeUtils.clean(accountNumber);  
    Log.infof("Iniciando retiro - AccountHash: %s, Amount: %s", HashUtils.sha256(sanitizedAccount), amount);

    AccountDomain account = accountRepositoryPort.findByNumber(sanitizedAccount)  
        .orElseThrow(() -> new AccountNotFoundException("Cuenta no encontrada"));

    AccountDomain updatedAccount = account.withdraw(amount);  
    accountRepositoryPort.save(updatedAccount);

    Log.infof("Retiro exitoso - AccountHash: %s", HashUtils.sha256(sanitizedAccount));  
    return updatedAccount;  
}