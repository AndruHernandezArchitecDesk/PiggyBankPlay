---
name: offline-first
description: Persistencia local, integridad y sincronización futura para PiggyBank Play (Expo / React Native / TypeScript).
---

# Persistencia local, integridad y sincronización futura

## Objetivo
Garantizar que los retos funcionen sin conexión y no se pierdan registros.
## Reglas obligatorias
- Usar Expo SQLite mediante repositorios; UI no ejecuta SQL.
- Crear migraciones versionadas y probadas; nunca borrar datos del usuario silenciosamente.
- Completar cuota y registrar movimiento en UNA transacción atómica.
- Definir claves primarias estables, constraints, índices y foreign keys activas.
- Evitar duplicados mediante `operationId` único y transacciones; no confiar solo en deshabilitar botón.
- Persistir montos en centavos y moneda explícita; registrar timestamps UTC.
- Guardar estado y log de eventos para auditoría y posible sincronización futura.
- Manejar fallos de escritura y espacio insuficiente; solo celebrar tras commit.
- No almacenar tokens o secretos en SQLite plano; usar almacenamiento seguro cuando corresponda.
- Sincronización futura: IDs globales, versiones, conflictos definidos y operaciones idempotentes; no implementarla prematuramente.
## Procedimiento
1. Diseñar esquema y migración.
2. Implementar repositorio y transacción.
3. Probar interrupción, duplicación, reapertura y migración.
4. Verificar consistencia de progreso calculado desde cuotas completadas.
## Definition of Done
Los datos sobreviven reinicios; operaciones repetidas no duplican dinero; errores no dejan estados parciales.
