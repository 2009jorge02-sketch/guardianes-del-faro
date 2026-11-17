---
id: TASK-008
titulo: MatchService — máquina de estados, noches y oleadas
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-005, TASK-007]
responsable: Codex
txx: T05
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-008 · Bucle de partida

## Objetivo
Orquestar una partida completa: Prep → Noche 1..5 → Intermedios → Victoria/Derrota → Resultados, con oleadas definidas por `Config`.

## Contexto
[[GDD]] §Bucle y §Condiciones; [[Mecanicas]] §Noches; remote `MatchState`: [[Cliente-Servidor]].

## Requisitos
1. `MatchService` con estados `Lobby, Prep(20 s, parámetro ≤ 30 s), Night(n), Intermission(25 s, ajustable 20–30 s), Victory, Defeat, Results`. Transiciones validadas y registradas.
2. Inicio: cuando hay ≥1 jugador y pulsa «Jugar» (`ReadyForRun`) o tras 15 s en Lobby con jugadores (configurable). Soporta 1–4 jugadores; unirse a mitad de partida = espectador hasta la siguiente (decisión simple documentada).
3. Cada noche: lee `Config.Nights[n]`; programador de spawn reparte `cantidad × (0.7+0.3·n_jugadores)` Sombras (y otros tipos cuando existan) a lo largo de la duración, respetando el tope; llama a `MapBuilder.setNight(n)`.
3b. **Oleadas en pulsos:** cada noche se reparte en 2–3 pulsos separados por 3–5 s de respiro (`Config.Nights[n].pulses`) para permitir recargar y leer la situación; el total de enemigos por noche no cambia.
4. Fin de noche: se deja de spawnear, los enemigos vivos se eliminan tras 5 s (amanecer); si Integridad>0 pasa a Intermission (o Victory tras la 5).
5. `Destroyed` ⇒ `Defeat` inmediato; transición a `Results` y botón de reinicio (`PlayAgain`) que resetea todo.
6. Difundir `MatchState {state, night, endsAt, integrity}` en cada cambio (marca de tiempo del servidor).
7. Durante Intermission (en este task) solo temporizador; las cartas llegan en [[TASK-011]].
8. Estadísticas por partida: sombras destruidas, noches superadas, tiempo.

## Componentes afectados (propuesta)
`src/server/Services/MatchService.luau`, `src/shared/Config.luau` (lectura), `src/server/Main.server.luau`, `tests/match_test.luau` (transiciones puras).

## Criterios de aceptación
- [ ] Una partida automática (sin interacción) recorre las 5 noches o termina en Derrota coherente con la Integridad.
- [ ] Los tiempos coinciden con [[Mecanicas]] (75/85/95/105/120 s; descanso 25 s) ±1 s.
- [ ] Reiniciar con `PlayAgain` deja el estado limpio (sin enemigos ni Integridad residual) 5 veces seguidas.
- [ ] Con 1, 2 y 4 jugadores el número de spawns coincide con el escalado.
- [ ] Sin errores en Output en 3 partidas completas.

## Pruebas
Unitarias de transiciones y escalado; manual: partidas completas, 1 y 4 clientes, salida de jugadores a mitad.

## Restricciones
Todo servidor; el cliente solo recibe estado. No implementar cartas ni persistencia aquí.

## Entregable
Rama `codex/task-008-match` + registro de 3 partidas.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
