---
tipo: planificacion
---
# Prototipo y MVP

## Definición del prototipo (Fase 1)
Una isla, un faro, linterna individual, los 3 enemigos de D18 (Rastreadora, Acechadora, Bruta; [[Mecanicas]] §Enemigos), 5 noches parametrizadas, Integridad, HUD y resultados mínimos, overlay de rendimiento. **Sin** persistencia, tienda real, pagos, cartas ni Foco Mayor ([[ADR-004-validacion-concepto]], confirmado por [[ADR-006-contrato-producto-v4]] D13). Tareas históricas: [[TASK-001]]–[[TASK-009]], [[TASK-012]] (correspondencia con T00–T21 en ADR-006).

## Puerta 1 (fin del prototipo) — todo debe cumplirse
- [ ] ≥30 FPS en móvil de gama baja (o emulador acordado) con 60 enemigos y 4 jugadores; resultado registrado en `07-Registro/Revisiones`.
- [ ] Una partida solo completa sin errores en consola (5 noches).
- [ ] Puerta de validación de [[ADR-006-contrato-producto-v4]] §Puerta de validación (≥5 externos, ≥2 en móvil, ≥2 en PC, ≥2 partidas cada uno; [[VALIDACION-PROTOTIPO]]) — anotado, no estadístico. *Antes: ≥3 prueban, ≥2 repetirían.*
- [ ] Sin remote que acepte datos no validados ([[Seguridad]]).

## Definición del MVP (Fase 2)
Prototipo + Foco Mayor + cartas temporales votadas + **salud, derribo, rescate y estación de reanimación** + **una expedición exterior completa** (ADR-006 D5/D6) + persistencia + XP/Monedas del Faro (Cristales de Luz solo en partida) + menú + personalización mínima + tutorial + ajustes + eventos mínimos de analítica comercial (propuesta, no amplía el alcance jugable; [[ADR-005-estrategia-comercial]]). Tareas: [[TASK-010]], [[TASK-011]] y siguientes en [[TASKS]].

## Puerta 2 (fin del MVP)
- [ ] 20 partidas seguidas sin error crítico.
- [ ] Guardado/carga verificados con fallos simulados.
- [ ] Accesibilidad mínima (daltonismo, reducir efectos).
- [ ] Revisión de políticas de monetización antes de añadir compras.
