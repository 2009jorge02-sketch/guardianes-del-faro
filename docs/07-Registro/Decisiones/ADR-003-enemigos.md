---
id: ADR-003
titulo: Simulación y render de enemigos masivos
estado: propuesta (con criterio de revisión medible)
fecha: 2026-11-14
decide: Claude
---
# ADR-003 · Enemigos

## Contexto
Hasta 60 enemigos con 4 jugadores en móvil. Los `Humanoid` no escalan ([[Revision-Finalistas]]). Riesgo R1 en [[Riesgos]].

## Opciones
- **A. Servidor mueve Parts ancladas (sin Humanoid) con `BulkMoveTo`** a 15–20 Hz. + simple, replicación automática. − ancho de banda del servidor crece con nº de enemigos.
- **B. Simulación en datos en servidor + snapshots comprimidos a clientes que renderizan modelos pooleados.** + mejor red/CPU. − más complejo, más difícil de depurar a ciegas.

## Decisión
**A para el prototipo y MVP**, con tope 60. Si [[TASK-012]] mide <30 FPS móvil o red saturada con 60 enemigos, **migrar a B** (nueva tarea) o bajar el tope. La API de `EnemyService` debe aislar la representación (interfaz `Spawn/Step/Damage/Despawn`) para que el cambio no afecte a `BeamService`.

## Consecuencias
Los enemigos se modelan como tablas `{id, tipo, pos, hp, ...}` en servidor desde el principio (datos primero, Parts como vista), lo que facilita B.
