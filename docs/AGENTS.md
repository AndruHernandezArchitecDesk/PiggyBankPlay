# PiggyBank Play — Instrucciones para agentes

Stack: Expo + React Native + TypeScript strict + Expo Router + Zustand + Expo SQLite + Zod + Reanimated. Arquitectura Feature First / Clean Architecture pragmática.

Antes de modificar código, lee la skill relevante en `.agents/skills/<nombre>/SKILL.md`.

Skills:
- `react-native-architect`: estructura y dependencias.
- `typescript-quality`: tipado, validaciones y estilo.
- `savings-engine`: cuotas y dinero (OBLIGATORIA al tocar ahorro).
- `game-design-ux`: gamificación y accesibilidad.
- `offline-first`: SQLite e integridad.
- `testing-security`: pruebas, CI y releases.

## Reglas globales
1. El usuario selecciona libremente cuotas; NO se asignan a días.
2. Marcar una cuota NO recalcula las demás.
3. Todos los importes son enteros en centavos y la suma de cuotas debe ser exacta.
4. Registrar cuotas completadas de forma transaccional e idempotente.
5. El dominio no depende de React Native ni SQLite.
6. No añadir backend, IA o complejidad sin un caso de uso aprobado.
7. Antes de finalizar cambios: typecheck, lint y pruebas relacionadas.
