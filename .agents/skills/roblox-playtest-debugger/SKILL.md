---
name: roblox-playtest-debugger
description: "Prueba, depura y mide Guardianes del Faro en Roblox Studio: errores de consola, rendimiento, jugabilidad, multijugador, controles táctiles y dispositivos de baja gama. Usa el servidor MCP integrado de Roblox Studio cuando esté conectado. Úsala para TASK-012, para criterios de rendimiento o ante un fallo en ejecución. No la uses para escribir funcionalidad nueva."
---

# roblox-playtest-debugger

Objetivo: **evidencia real** (logs, mediciones, capturas descritas), nunca cifras supuestas.

## Antes de empezar
1. Lee la tarea o el error que motiva la prueba y sus criterios de aceptación.
2. Presupuestos y objetivos: `docs/04-Arquitectura/Rendimiento.md` (≥ 30 FPS móvil con 60 enemigos y 4 jugadores; ≥ 60 FPS en PC; ≤ 6 luces dinámicas; ≤ 60 enemigos). Plan de playtest: `docs/05-Planificacion/VALIDACION-PROTOTIPO.md`; herramientas de medida: `docs/06-Tareas/TASK-012.md`.
3. Comprueba si el MCP de Studio está disponible (`docs/04-Arquitectura/Roblox-Studio-MCP.md`). Es **distinto de Rojo**: Rojo sincroniza archivos; el MCP deja a un agente leer y actuar en un Studio abierto.

## Con MCP de Studio conectado
Orden de uso, de menor a mayor impacto (detalle de herramientas en `references/studio-mcp.md`):
1. **Solo lectura**: `list_roblox_studios`, `get_studio_state`, `get_console_output`, `search_game_tree`, `inspect_instance`, `script_read`/`script_grep`, `screen_capture`.
2. **Ejecución de la prueba**: `start_stop_play` (Play/Stop) y entrada simulada (`character_navigation`, `user_keyboard_input`, `user_mouse_input`) para recorrer el flujo de la tarea.
3. **Modifican el lugar abierto** (`execute_luau` en Edit, `multi_edit`, `insert_asset`, `save_place`): **solo con autorización del usuario** para esa acción. `execute_luau` en Client/Server de una sesión de juego sirve para medir sin tocar el lugar; aun así, no cambies datos que no hayas creado para la prueba.
Sin MCP: dame al usuario pasos exactos de Studio (Test → Play, 1 y 4 jugadores) y pídele logs o capturas.

## Qué probar
- **Errores**: consola limpia al jugar la tarea completa; reproduce, aísla y corrige la causa, no el síntoma.
- **Rendimiento**: MicroProfiler y estadísticas de Studio con el nº de enemigos objetivo; mide tiempo de servidor por paso y FPS de cliente. Registra equipo y condiciones.
- **Multijugador**: 1 y 4 clientes (Studio → Test → Local Server). Comprueba que lo que ve cada cliente es coherente y que el cliente no decide daño ni economía.
- **Táctil**: emulador de dispositivos de Studio (retrato/paisaje, móvil gama baja); botones ≥ 48 px, linterna jugable con un pulgar (esquemas A/B en `Mecanicas.md`). Una prueba en móvil real es del usuario.
- **Gama baja**: opción «reducir efectos» y presupuestos de luces y partículas.

## Registro y entrega
- Cada sesión: nota `docs/07-Registro/Pruebas/` con la plantilla `prueba`; cada fallo: `docs/07-Registro/Errores/` con la plantilla `error` (`tipo: error`, `tarea`).
- Si un criterio de rendimiento falla, aplica el fallback de `ADR-003-enemigos.md` o propone bajar el tope; no cambies presupuestos por tu cuenta.

## Verificación
Cada afirmación del informe debe poder rastrearse a una salida de consola, medición o paso reproducible. Lo no probado se declara «no verificado».

## Límites
No concedas permisos de MCP ni cambies ajustes de Studio por tu cuenta. No modifiques proyectos de Studio sin autorización. Nada de commits ni push.
