---
name: game-design-ux
description: Gamificación ética, animaciones y accesibilidad para PiggyBank Play (Expo / React Native / TypeScript).
---

# Gamificación ética, animaciones y accesibilidad

## Objetivo
Hacer el ahorro divertido y sostenible, sin presión económica ni patrones manipulativos.
## Reglas obligatorias
- Autonomía: el usuario elige la cuota; nunca imponer ahorro diario.
- Competencia: mostrar progreso real y celebraciones proporcionadas.
- Recompensas cosméticas por constancia/logros, sin apuestas, loot boxes pagadas ni premios monetarios aleatorios.
- Evitar penalizaciones por días sin ahorrar, culpa, FOMO o notificaciones excesivas.
- Animar después de confirmar persistencia; reducir movimiento si el sistema lo solicita.
- Soportar lectores de pantalla, contraste adecuado, targets táctiles accesibles y texto escalable.
- Preferir Reanimated para transiciones; usar Rive/Lottie solo cuando aporte valor y medir FPS en dispositivos modestos.
- Respetar sonido apagado y controles de vibración/animación.
- Nunca mostrar ahorro ficticio como real.
## Procedimiento
1. Definir objetivo conductual verificable (p. ej. completar primera cuota).
2. Diseñar flujo sin fricción y estado vacío/error.
3. Añadir feedback visual y accesible.
4. Probar rendimiento, reduced motion y usabilidad.
5. Medir retención y finalización sin manipulación.
## Definition of Done
Flujo funcional sin animaciones, accesible y sin recompensas que alteren saldos.
