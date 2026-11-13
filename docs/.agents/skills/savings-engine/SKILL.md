---
name: savings-engine
description: Motor matemático y reglas de ahorro para PiggyBank Play (Expo / React Native / TypeScript).
---

# Motor matemático y reglas de ahorro

## Objetivo
Generar cuotas libres que suman exactamente la meta, sin fechas asignadas ni recálculo al completarlas.
## Invariantes
- Usar enteros en unidades menores (centavos para USD), nunca float para dinero.
- Entrada: `targetMinor`, `installmentCount`, `minMinor`, `maxMinor`, moneda y plazo opcional.
- Validar enteros positivos y `count * min <= target <= count * max` con protección ante overflow.
- Generar exactamente `count` cuotas en `[min,max]`, suma EXACTA `target`.
- No asociar cuota a día; el plazo solo es fecha objetivo.
- Completar cualquier cuota disponible, varias el mismo día; jamás redistribuir las restantes.
- Cada cuota tiene ID estable y estado `available|completed`.
- Completar debe ser idempotente mediante identificador de operación; evitar dobles aportes.
- Permitir deshacer con operación explícita y registro de auditoría.
- Las recompensas virtuales nunca alteran los importes.
## Algoritmo recomendado
Inicializar `count` cuotas con `min`; distribuir `remaining = target-count*min` entre cuotas elegidas al azar, cada una hasta `max-min`; mezclar posiciones al final. Usar aleatoriedad adecuada para UX, no criptográfica; soportar semilla inyectable en tests. Para grandes valores evitar bucles por centavo: asignar incrementos acotados y garantizar capacidad remanente.
## Pruebas mínimas
- Casos frontera: meta mínima/máxima, cuotas iguales, 1 cuota, datos inválidos.
- Property-based: longitud, rango, suma exacta para miles de entradas válidas.
- Completar cuota de $5 entre otras no altera montos/estados restantes.
- Completar dos veces no duplica ahorro; múltiples cuotas el mismo día funcionan.
- Fecha límite vencida no elimina dinero registrado.
## Definition of Done
Invariantes verificadas por tests unitarios independientes de UI y SQLite.
