---
id: TASK-009
titulo: HUD mínimo y pantalla de resultados
estado: lista
prioridad: media
fase: 1
depende_de: [TASK-006, TASK-008]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-009 · HUD y resultados

## Objetivo
Mostrar al jugador la información esencial y cerrar la partida con una pantalla de resultados y «Otra partida».

## Contexto
Diseño de interfaz: [[Arte-UI-Audio]] §Interfaz. Estados: [[TASK-008]]. Accesibilidad: [[Experiencia-Jugador]].

## Requisitos
1. `HudController`: barra de Integridad del Faro, «Noche N/5» y cuenta atrás, barra de Carga junto al botón de linterna, contador de Sombras destruidas; todo desde `MatchState` y atributos.
2. Feedback de daño al faro: sacudida de cámara leve y viñeta roja breve al cambiar `LastHit` (con opción de reducir efectos desactivada por ahora, pero preparada por `Settings.reduceEffects`).
3. Pantalla de resultados (`ResultsScreen`): victoria/derrota, noches superadas, Sombras destruidas, tiempo; botón «Otra partida» (`PlayAgain`). Sin recompensas aún (marcador de posición «Luz y Cristales: próximamente»).
4. Mensajes de tutorial contextual (máx. 3) durante la noche 1: «Mantén pulsado para encender la linterna», «Apunta hacia las Sombras», «Protege el faro».
5. UI escalable (`UIScale`/anclajes) legible en móvil: botones ≥48 px, texto ≥16 px equivalente; sin parpadeos >3 Hz.
6. Estilo provisional coherente con la paleta de [[Arte-UI-Audio]].

## Componentes afectados (propuesta)
`src/client/Controllers/{HudController,ResultsScreen}.luau`, `src/client/Main.client.luau`.

## Criterios de aceptación
- [ ] Todos los elementos reflejan el estado real (verificado en partida completa).
- [ ] En emulador móvil vertical y horizontal no hay elementos fuera de pantalla ni solapados con el botón de linterna.
- [ ] El botón «Otra partida» reinicia con éxito.
- [ ] Ningún parpadeo por encima de 3 Hz.

## Pruebas
Partida completa en PC y emulador móvil; capturas descritas.

## Restricciones
Sin lógica de juego en UI; sin recursos externos; textos en español.

## Entregable
Rama `codex/task-009-hud`.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
