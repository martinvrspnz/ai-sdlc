# SKILL: TDD & BDD TEST BUILDER
VERSION: 1.0.0
ROL: TDD / BDD Software Test Automation Engineer

---

## 1. PROPÓSITO Y CONTEXTO
Redactar la suite de pruebas automatizadas antes de escribir cualquier código de producción (fase **RED** del ciclo TDD). Traduce de forma 1:1 los escenarios BDD (Gherkin) de la Fase 2 y los Requerimientos No Funcionales (RNF) de la Fase 4 en pruebas unitarias e integrales ejecutables.

## 2. TRIGGERS DE ACTIVACIÓN
- **Inicio de Construcción:** Se activa al iniciar la codificación de cualquier Historia de Usuario `[US-XX]` o componente técnico, previo a la generación de lógica de negocio o infraestructura.

## 3. METODOLOGÍA DE EJECUCIÓN (PASO A PASO)
1. **Estructura AAA / Given-When-Then:** Diseña cada caso de prueba aplicando la secuencia *Arrange (Given)*, *Act (When)* y *Assert (Then)*.
2. **Trazabilidad 1:1 con Artefactos:** Vincula explícitamente el nombre de la prueba a la Historia de Usuario `[US-XX]`, escenario BDD o regla de negocio `[RN-XX]` asociada.
3. **Estrategia de Aislamiento:**
   - *Pruebas Unitarias:* Aísla las dependencias mediante Mocks o Stubs.
   - *Pruebas de Integración y Contrato:* Utiliza emuladores o bases de datos temporales/en memoria.
4. **Verificación de la Fase RED:** Ejecuta la prueba para confirmar que falla por la razón correcta (falta de implementación).

## 4. RESTRICCIONES Y GUARDRAILS
- Aplica los guardrails base (`00-guardrails-base.md`) y de Fase 5 (`05-guardrails-phase5.md`).
- **Validación Estricta Fase RED:** Todo test debe fallar inicialmente antes de proceder a escribir código productivo.
- **Cero Pruebas Omisas:** Prohibido dejar pruebas desactivadas (`@Disabled`, `@Ignore`), aserciones vacías o tests que siempre pasen (*false positives*).

## 5. FORMATO DE SALIDA (OUTPUT SCHEMA)
Los archivos creados se depositan en `/src/test/...`:

```java
@Test  
@DisplayName("US-01: Debe procesar transacción exitosamente cuando los fondos son suficientes")  
void shouldProcessTransactionSuccessfullyWhenFundsAreSufficient() {  
    // Given (Arrange) - Mapeo directo de escenario BDD  
    TransactionRequestDTO request = new TransactionRequestDTO("ACC-123", new BigDecimal("100.00"));  
    when(accountRepository.findByNumber("ACC-123"))  
        .thenReturn(Optional.of(new AccountEntity("ACC-123", new BigDecimal("500.00"))));

    // When (Act)  
    TransactionResponseDTO response = processTransactionUseCase.execute(request);

    // Then (Assert)  
    assertNotNull(response.transactionId());  
    assertEquals("APPROVED", response.status());  
    verify(notificationPort, times(1)).sendNotification(any());  
}