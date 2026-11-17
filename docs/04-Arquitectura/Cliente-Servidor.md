---
tipo: arquitectura
---
# Cliente–Servidor

Principio: **servidor autoritativo**. Ver [[ARCHITECTURE]], [[Seguridad]].

## Responsabilidades
| Servidor | Cliente |
|---|---|
| Estado de partida, oleadas, enemigos (posición, PV), daño, Carga, Integridad, cartas, recompensas, persistencia | Entrada, cámara, HUD, visuales y sonido del haz, interpolación visual, feedback |

## Remotes (nombres únicos en `Shared/Remotes`)
| Remote | Dir. | Tipo | Carga útil | Validación en servidor |
|---|---|---|---|---|
| `BeamInput` | C→S | UnreliableRemoteEvent | `{on: boolean, dir: Vector3}` (≤20 Hz) | tipos; `dir` finito y normalizado; estado de partida = Night; jugador activo (no derribado ni eliminado); no sobrecalentado; límite 25 msg/s |
| `SpotlightToggle` | C→S | RemoteEvent | `{enter: boolean}` | distancia a la escalera; plaza libre; jugador activo; cooldown 1 s |
| `SpotlightAim` | C→S | UnreliableRemoteEvent | `{dir: Vector3}` | solo si es el operador; normalización; límite 20 msg/s |
| `CardVote` | C→S | RemoteEvent | `{cardId: string}` | solo en Intermission; id en la oferta actual; un voto por jugador |
| `ReadyForRun` / `PlayAgain` | C→S | RemoteEvent | — | estado válido; límite 1 msg/s |
| `MatchState` | S→C | RemoteEvent | `{state, night, endsAt, integrity}` | — |
| `CardOffer` | S→C | RemoteEvent | `{cards, endsAt}` | — |
| `BeamState` | S→C | UnreliableRemoteEvent | `{userId, on, dir}` por jugador (para visuales de otros) | difundido solo a jugadores del servidor |
| `PlayerStateChanged` | S→C | RemoteEvent | `{userId, state, until?}` con state = activo/derribado/eliminado | — · *antes `PlayerStunned`; los remotes de rescate y reanimación los define T10* |
| `RunResults` | S→C | RemoteEvent | recompensas, estadísticas | — |

Regla: **ningún remote permite al cliente enviar daño, posición de enemigos, recompensas ni identificadores de otros jugadores.** `RemoteFunction` solo si es imprescindible, con timeout.

## Tiempos
Servidor: bucle de simulación a 20 Hz para enemigos/daño (`Heartbeat` con acumulador); marcas de tiempo con `workspace:GetServerTimeNow()` para temporizadores replicados.

## Enemigos
Decisión y fallback en [[ADR-003-enemigos]].
