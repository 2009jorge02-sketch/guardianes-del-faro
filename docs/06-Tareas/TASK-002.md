---
id: TASK-002
titulo: Módulos compartidos — Config, Types, Remotes y utilidades
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-001]
responsable: Codex
txx: T02
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-002 · Config, Types, Remotes, utilidades

## Objetivo
Crear la base compartida: valores de balance centralizados, tipos, definición de remotes y utilidades reutilizables (Pool, RateLimiter, Signal).

## Contexto
Fuente única de cifras: [[Mecanicas]]. Remotes: [[Cliente-Servidor]]. Seguridad: [[Seguridad]]. Estructura: [[ARCHITECTURE]].

## Requisitos
1. `src/shared/Config.luau`: tabla inmutable (congelada con `table.freeze`) con: constantes de linterna, Foco Mayor, Integridad, estados de jugador (salud, derribo, eliminación; D5/D15), enemigos (Rastreadora, Acechadora y Bruta —antes Sombra, Reptante y Bruto— con sus valores), `Nights` (duración, spawn base, tipos), `Beam.overlapBonus` (1.0 por defecto), `Input.touchScheme` ("A"), `Nights[n].pulses` (2–3, respiro 3–5 s), escalado por jugadores `0.7 + 0.3*n`, tope de enemigos 60, anillo de spawn radio 60, cartas. Valores **exactamente** los de [[Mecanicas]].
2. `src/shared/Types.luau`: tipos Luau para Enemigo, EnemyDef, NightDef, MatchState, Card, BeamInput.
3. `src/shared/Remotes.luau`: crea (servidor) u obtiene (cliente) todos los remotes de [[Cliente-Servidor]] bajo `ReplicatedStorage.Remotes`, con `UnreliableRemoteEvent` donde se indica. API: `Remotes.get(name)`.
4. `src/shared/Util/Pool.luau` (pool genérico con `acquire/release`), `RateLimiter.luau` (token bucket por clave), `Signal.luau` (señal simple).
5. Pruebas unitarias en `tests/` para Pool, RateLimiter y escalado por jugadores (n=1→1.0, n=4→1.9).
6. Todos los módulos con `--!strict`.

## Componentes afectados (propuesta)
`src/shared/Config.luau`, `Types.luau`, `Remotes.luau`, `src/shared/Util/{Pool,RateLimiter,Signal}.luau`, `tests/*`.

## Criterios de aceptación
- [ ] `Config` coincide con [[Mecanicas]] (el informe incluye tabla comparativa).
- [ ] Las pruebas unitarias pasan (adjuntar salida).
- [ ] Los remotes existen con los nombres y tipos de [[Cliente-Servidor]] al iniciar el servidor.
- [ ] `stylua --check` y `selene` sin avisos (si instalados).
- [ ] Ningún módulo usa globales.

## Pruebas
Ejecutar `tests/run.luau`; en Studio, comprobar en el Explorer la carpeta `ReplicatedStorage.Remotes`.

## Restricciones
No añadir lógica de juego; no cambiar valores de balance sin actualizar primero [[Mecanicas]] (pregunta a Claude).

## Entregable
Rama `codex/task-002-shared` con los módulos y pruebas.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
