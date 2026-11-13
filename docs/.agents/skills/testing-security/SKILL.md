---
name: testing-security
description: Pruebas, seguridad, CI y publicación para PiggyBank Play (Expo / React Native / TypeScript).
---

# Pruebas, seguridad, CI y publicación

## Objetivo
Evitar regresiones, errores financieros y entregas inestables.
## Pirámide de pruebas
- Unitarias: motor, validaciones, use cases (Jest).
- Componentes: tableros, estados, accesibilidad (React Native Testing Library).
- Integración: repositorio SQLite y migraciones en entorno compatible.
- E2E: crear reto, completar cuota, reiniciar, recuperar progreso (Maestro).
## Reglas obligatorias
- Ejecutar en CI: install con lockfile, typecheck, lint, tests y comprobación de Expo.
- Cubrir invariantes del ahorro con property-based tests (p. ej. fast-check).
- Nunca poner secretos en repositorio, bundle ni variables públicas `EXPO_PUBLIC_*`.
- Mantener dependencias actualizadas y revisar permisos solicitados.
- No registrar PII ni importes detallados en analítica sin consentimiento.
- Añadir manejo de errores y pruebas de accesibilidad en flujos críticos.
- Usar EAS Build con perfiles dev/preview/production y versionado coherente.
## Definition of Done
CI verde, tests de dinero y persistencia verdes, ningún secreto expuesto, release reproducible.
