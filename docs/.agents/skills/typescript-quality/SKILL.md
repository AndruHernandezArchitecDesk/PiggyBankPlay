---
name: typescript-quality
description: Calidad de código TypeScript para PiggyBank Play (Expo / React Native / TypeScript).
---

# Calidad de código TypeScript

## Objetivo
Código legible, seguro y fácil de mantener.
## Reglas obligatorias
- Activar `strict`, `noUncheckedIndexedAccess` y `exactOptionalPropertyTypes` cuando sea compatible.
- Prohibir `any` no justificado; preferir `unknown` y narrowing.
- Validar datos externos con Zod en fronteras (persistencia, API, deep links).
- Usar tipos discriminados para estados de carga/error/éxito.
- Mantener funciones pequeñas, sin números mágicos y con responsabilidades claras.
- Preferir inmutabilidad y funciones puras para cálculos.
- Usar ESLint, Prettier y convenciones de nombres consistentes.
- No registrar datos privados en logs; no esconder errores con `catch` vacío.
## Procedimiento
1. Definir contratos y casos límite.
2. Implementar sin casts inseguros.
3. Añadir tests de errores y entradas inválidas.
4. Ejecutar `tsc --noEmit`, lint y tests.
## Definition of Done
- Sin errores de tipos ni lint.
- Errores controlados y mensajes claros.
- Código comprensible sin comentarios redundantes.
