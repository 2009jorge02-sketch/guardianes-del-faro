---
id: TASK-007
titulo: LighthouseService — Integridad y daño de enemigos al faro
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-005]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-007 · Integridad del Faro

## Objetivo
El faro tiene Integridad; los enemigos que llegan le hacen daño continuo y al llegar a 0 se declara derrota.

## Contexto
[[Mecanicas]] §Integridad y §Enemigos (daño por tipo). Estados de partida: [[ARCHITECTURE]].

## Requisitos
1. `LighthouseService`: `integrity` y `maxIntegrity` (100) desde `Config`; API `damage(amount)`, `repair(amount)`, `addMax(amount)`, señal `Destroyed`, atributo replicado `Integrity` en `Workspace.Map.Lighthouse`.
2. Suscribirse a `ReachedLighthouse` de [[TASK-005]]: el enemigo se «pega» al faro y aplica su daño/s (valor de `Config` por tipo) cada 0,25 s hasta morir.
3. Feedback mínimo en servidor: atributo `LastHit` (timestamp) para que el cliente lo use en efectos (el efecto se hace en [[TASK-009]]).
4. Reinicio: `reset()` restaura valores para una nueva partida.
5. Pruebas unitarias del cálculo de daño y límites (nunca <0 ni >máx).

## Componentes afectados (propuesta)
`src/server/Services/LighthouseService.luau`, `tests/lighthouse_test.luau`.

## Criterios de aceptación
- [ ] 10 Sombras pegadas al faro lo destruyen en el tiempo esperado por `Config` (cálculo en el informe).
- [ ] `Destroyed` se emite una sola vez.
- [ ] `repair` y `addMax` respetan límites.
- [ ] El atributo `Integrity` cambia en cliente y servidor.

## Pruebas
Unitarias + `debugSpawn` y observar la Integridad.

## Restricciones
Valores solo desde `Config`; sin UI aquí.

## Entregable
Rama `codex/task-007-lighthouse`.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
