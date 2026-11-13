# PiggyBank Play — Arquitectura técnica v1

## Visión
Aplicación de retos de ahorro gamificados, offline-first, sin custodiar dinero. El usuario define meta, cantidad de cuotas, mínimo, máximo y fecha objetivo opcional. El motor genera cuotas cuya suma coincide exactamente con la meta. El usuario marca cualquier cuota cuando quiera, sin recálculo.

## Stack
- Expo + React Native + TypeScript estricto
- Expo Router, Zustand (estado de UI), Zod (validación de entradas)
- Expo SQLite (persistencia), Reanimated + Gesture Handler (interacción)
- Rive/Lottie opcional, según compatibilidad y rendimiento
- Jest + React Native Testing Library + Maestro + GitHub Actions

## Capas por feature
`domain` (entidades, invariantes, contratos) → `application` (casos de uso) → `infrastructure` (SQLite/adaptadores) y `presentation` (UI/hooks). Las dependencias apuntan al dominio; la UI nunca contiene cálculos monetarios.

## Estructura sugerida
```
src/
  app/                      # Rutas Expo Router
  features/
    challenges/{domain,application,infrastructure,presentation}/
    contributions/{domain,application,infrastructure,presentation}/
    rewards/{domain,application,infrastructure,presentation}/
    piggy/{presentation}/
  shared/{theme,components,utils}/
  infrastructure/database/
assets/{images,animations,sounds}/
tests/{unit,integration,e2e}/
```

## Modelo mínimo
- `Challenge`: id, title, currency, targetMinor, installmentCount, minMinor, maxMinor, targetDate?, createdAt, status.
- `Installment`: id, challengeId, amountMinor, status, completedAt?.
- `ContributionEvent`: id/operationId, installmentId, amountMinor, type, createdAt.
- `RewardUnlock`: id, rewardId, challengeId?, unlockedAt.

## Invariantes
`count * min <= target <= count * max`; `sum(installments.amountMinor) === targetMinor`; importes enteros; cuotas sin fechas; completar no modifica las restantes; persistencia idempotente y transaccional.

## Fases
1. Configurar proyecto, lint, typecheck, CI.
2. Motor de cuotas y property-based tests.
3. SQLite, migraciones y tablero funcional.
4. Animaciones, mascota y recompensas cosméticas.
5. Accesibilidad, notificaciones opcionales, E2E y publicación.

## Decisiones aplazadas
Backend Spring Boot/PostgreSQL, autenticación, sincronización, social, monetización. Definirlas con evidencia de uso.
