---
id: TASK-005
titulo: EnemyService — spawn, movimiento por lotes y enemigo Sombra Rastreadora (antes «Sombra»)
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-002, TASK-003]
responsable: Codex
txx: T05
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-005 · EnemyService y Sombra

## Objetivo
Sistema de enemigos masivos sin `Humanoid`, con pooling y movimiento por lotes, y el primer tipo (Sombra).

## Contexto
Decisión: [[ADR-003-enemigos]] (opción A). Valores: [[Mecanicas]] §Enemigos. Presupuestos: [[Rendimiento]].

## Requisitos
1. `src/server/Services/EnemyService.luau` con API: `spawn(typeId, spawnIndex)`, `step(dt)`, `damage(enemyId, amount)`, `despawn(enemyId)`, `getAll()` (lectura), `count()`, señales `Killed(enemy)` y `ReachedLighthouse(enemy)`.
2. Representación: tablas `{id, typeId, pos: Vector3, hp, speedMul, alive}` como fuente de verdad; cada enemigo tiene una `Part` anclada (o modelo de ≤5 partes) obtenida de un `Pool` precalentado (80 piezas). La vista se actualiza con `workspace:BulkMoveTo` en lotes a 15–20 Hz.
3. Movimiento: línea recta hacia el centro del faro a la velocidad de `Config`; **+25 % de velocidad si no está iluminado** (flag `lit` actualizado por `BeamService`; por ahora siempre false).
4. Tope de 60 vivos (`Config`); `spawn` rechaza por encima del tope (devuelve nil y registra).
5. Al llegar a distancia ≤ radio base del faro (6): emitir `ReachedLighthouse` (el daño lo aplica [[TASK-007]]).
6. Comando de depuración (solo Studio) `debugSpawn(n)` para generar n Sombras en el anillo.
7. Pruebas unitarias del movimiento y del tope.

## Componentes afectados (propuesta)
`src/server/Services/EnemyService.luau`, `src/shared/Config.luau` (solo lectura), `tests/enemy_test.luau`.

## Criterios de aceptación
- [ ] `debugSpawn(60)` crea 60 Sombras que caminan hacia el faro sin errores.
- [ ] Tiempo medio de servidor por `step` con 60 enemigos <2 ms (medido y reportado).
- [ ] No hay creación/destrucción de instancias en caliente (pool): contador de `Instance.new` en `step` = 0.
- [ ] Tope de 60 respetado.
- [ ] No se usa `Humanoid` ni `Touched`.

## Pruebas
Pruebas unitarias; en Studio, `debugSpawn(60)` y medir con el `MicroProfiler`/script de temporización.

## Restricciones
Interfaz pública estable (ver [[ADR-003-enemigos]]) para poder cambiar la representación; sin pathfinding.

## Entregable
Rama `codex/task-005-enemies` con medición adjunta.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
