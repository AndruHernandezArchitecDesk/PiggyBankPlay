---
name: react-native-architect
description: Arquitectura y límites de dependencias para PiggyBank Play (Expo / React Native / TypeScript).
---

# Arquitectura y límites de dependencias

## Objetivo
Mantener una arquitectura Feature First con dominio puro y dependencias hacia adentro.
## Reglas obligatorias
- Usar Expo, React Native, TypeScript strict y Expo Router; `src/app` solo declara rutas y composición.
- Cada feature se divide en `domain`, `application`, `infrastructure`, `presentation` cuando la complejidad lo amerite.
- `domain` no importa React, Expo, SQLite, Zustand, navegación ni librerías de UI.
- `application` orquesta casos de uso y depende de contratos definidos en dominio.
- `infrastructure` implementa repositorios; `presentation` llama casos de uso mediante hooks/adaptadores.
- No crear abstracciones vacías, servicios globales mutables ni dependencias circulares.
- Separar componentes presentacionales de lógica; usar inyección de dependencias por composición explícita.
## Procedimiento
1. Identificar feature y reglas de negocio.
2. Definir entidades, contratos y casos de uso.
3. Implementar repositorio y adaptadores.
4. Crear UI y pruebas.
5. Verificar imports y dependencias.
## Definition of Done
- No imports de infraestructura o presentación desde dominio.
- Tests del dominio ejecutan sin runtime de React Native.
- Cambios pequeños, nombres explícitos y documentación de decisiones importantes.
