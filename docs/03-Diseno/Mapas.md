---
tipo: diseno
estado: especificación del mapa del MVP
---
# Mapas

## Isla del Faro (único mapa del MVP)
- Isla circular, **radio ≈ 45 studs** (diámetro 90). Justificación: caben 4 jugadores moviéndose sin amontonarse y los enemigos recorren los 60 studs de spawn al faro en ~7 s (Sombra a 8 studs/s) — tiempo suficiente para leer la amenaza y reaccionar.
- **Faro** en el centro (base radio 6, altura ≈ 40). Puerta/escalera al Foco Mayor en la galería (altura ≈ 30).
- **Anillo de spawn** de Sombras a radio 60 en el mar (10 puntos de aparición, direcciones aleatorias pero equilibradas).
- Elementos: muelle (decoración), 4 rocas bajas (cobertura visual, **no** colisionan con enemigos para evitar *pathfinding*), faroles apagados (se encienden con las mejoras: «Reflector»).
- Sin obstáculos que exijan navegación: enemigos van en línea recta al Faro (rendimiento y claridad).
- Transiciones: noche 1 al atardecer → noche 5 en tormenta total (Lighting y `Atmosphere` por noche).
- **Construcción en el prototipo:** generada por script (grayboxing) para que Codex pueda crearla sin Studio manual ([[ARCHITECTURE]]); arte final posterior.

## Futuros mapas (post-MVP, [[ROADMAP]])
«Arrecife» (viento lateral) y «Puerto» (más estrecho). Solo tras validar el núcleo.

## Relacionado (añadido en la mejora del vault)
- Recursos 3D de este mapa: [[RES-003-Isla-del-Faro]] · [[RES-001-Faro-principal]] · [[RES-004-Muelle]] · [[RES-005-Rocas-bajas]] · [[RES-006-Faroles-Reflector]] · Canvas: [[Diseno-de-Escenarios.canvas]]
