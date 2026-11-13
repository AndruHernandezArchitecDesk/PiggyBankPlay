# 🐷 PiggyBank Play

Aplicación móvil de retos de ahorro personal: convierte una meta en un tablero de cuotas libres.
El usuario elige qué cuota completar cuando tiene dinero; marcar una cuota **no recalcula** las demás.

> *Tu meta. Tu ritmo. Tu juego.*

## Stack

- Expo SDK 58 + React Native + TypeScript estricto
- Expo Router (rutas en `src/app/`)
- Zustand (estado de UI), Zod (validación en fronteras)
- Expo SQLite (persistencia local, offline-first)
- Reanimated (animaciones), Expo Haptics, Expo Notifications
- Jest + fast-check (pruebas unitarias y property-based)

## Comandos

```bash
npm install        # dependencias
npx expo start     # servidor de desarrollo
npm test           # pruebas
npm run typecheck  # tsc --noEmit
npm run lint       # eslint (expo lint)
npx expo-doctor    # diagnóstico del proyecto
```

## Estructura

```
src/
  app/                     # Rutas Expo Router (pantallas)
  features/
    challenges/
      domain/              # Entidades, invariantes, generador de cuotas (sin RN ni SQLite)
      application/         # Casos de uso: crear, completar, deshacer, resumir
      presentation/        # Hooks, store del borrador y componentes de UI
    settings/              # Preferencias del usuario (zustand)
  infrastructure/
    database/              # Migraciones y repositorio SQLite
    notifications/         # Recordatorios locales opcionales
    settings/              # Almacenamiento de preferencias (kv-store)
  shared/                  # Tema, componentes de UI y utilidades (dinero, fechas, ids)
```

## Reglas de negocio (no negociables)

1. Las cuotas pertenecen al tablero, no al calendario.
2. Marcar una cuota no recalcula las demás.
3. Los importes son enteros en centavos y la suma es exacta (`count × min ≤ meta ≤ count × max`).
4. Registrar y deshacer es transaccional e idempotente por `operationId`.
5. El dominio no depende de React Native ni de SQLite.
6. La app registra ahorros manualmente: no custodia ni transfiere dinero.

Arquitectura completa en [`ARQUITECTURA.md`](./ARQUITECTURA.md) e instrucciones para agentes en [`AGENTS.md`](./AGENTS.md) con skills en `.agents/skills/`.

## Recorrido MVP

Bienvenida → Inicio → Crear reto (presets Relax/Normal/Turbo/Personalizado) → Vista previa y
regeneración de cuotas → Tablero (confirmar ahorro / deshacer) → Historial → Ajustes
(moneda, recordatorios, accesibilidad, privacidad).

## Roadmap

- **MVP:** lo anterior, con persistencia local y funcionamiento sin conexión.
- **1.1:** accesorios, temas, insignias, estadísticas y múltiples monedas por reto.
- **2:** retos compartidos opcionales y sincronización con consentimiento.

## Nota

El nombre *PiggyBank Play* está pendiente de verificación comercial antes de publicar.
