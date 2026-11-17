---
id: TASK-001
titulo: Andamiaje del proyecto Rojo y configuración de herramientas
estado: lista
prioridad: alta
fase: 1
depende_de: []
responsable: Codex
txx: T02
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-15
---
# TASK-001 · Andamiaje Rojo y herramientas

## Objetivo
Dejar el repositorio listo para desarrollar en Luau con Rojo, con formato, lint y pruebas configurados, sin lógica de juego.

## Contexto
Codex trabaja con archivos en Git y se sincroniza con Studio mediante Rojo ([[ADR-002-herramientas]]). Estructura objetivo en [[ARCHITECTURE]]. El repo ya contiene `docs/`, `CLAUDE.md`, `AGENTS.md`, `.gitignore`.

## Requisitos
1. Crear `default.project.json` (Rojo) que mapee: `src/shared`→`ReplicatedStorage.Shared`, `src/server`→`ServerScriptService.Server`, `src/client`→`StarterPlayer.StarterPlayerScripts.Client`. Nombre del proyecto: `GuardianesDelFaro`.
2. Crear carpetas con un `Main.server.luau` y un `Main.client.luau` mínimos que impriman `[Faro] server/client iniciado`.
3. **Ya creados por Claude y verificados** (no recrear; solo comprobar y ajustar si fallan con el código real): `rokit.toml` (rojo 7.7.1, StyLua 2.6.0, selene 0.32.0), `stylua.toml`, `selene.toml` (std `roblox`), `.luaurc` (strict), `.gitattributes` (LF para Luau). Las herramientas y el plugin de Rojo **ya están instalados** en la máquina del usuario ([[Setup-Entorno]]).
4. Ejecutar `rokit install` si hace falta y confirmar versiones (`rojo --version`, `stylua --version`, `selene --version`).
5. Crear `tests/` con un runner Luau ligero (`tests/run.luau`) y una prueba de ejemplo; **no hay CLI `luau` instalado** (ver [[ADR-002-herramientas]]): si Codex necesita uno, debe proponerlo con justificación y pedir autorización al usuario; mientras tanto, diseñar las pruebas como módulos puros ejecutables desde Studio (script de pruebas en `tests/`) y documentar el procedimiento.
6. Revisar `docs/04-Arquitectura/Setup-Entorno.md` (ya escrito por Claude) y corregir lo que no coincida con la realidad.
7. Crear `.gitignore` adicional solo si hace falta (`sourcemap.json` ya incluido).
8. Dejar un `rojo build -o build/Guardianes.rbxl` funcional (`build/` y `*.rbxl` ya están en `.gitignore`; solo comprobarlo).

## Componentes afectados (propuesta)
Crear: `default.project.json`, `src/**/Main.*.luau`, `tests/run.luau`. Ya existen (solo verificar): `stylua.toml`, `selene.toml`, `.luaurc`, `rokit.toml`, `docs/04-Arquitectura/Setup-Entorno.md`.

## Criterios de aceptación
- [ ] `rojo build -o build/Guardianes.rbxl` finaliza sin errores (si Rojo está instalado) y el árbol coincide con lo descrito.
- [ ] `stylua --check src` y `selene src` pasan (si están instalados).
- [ ] Al hacer Play en Studio con Rojo conectado, la consola muestra ambos mensajes `[Faro]`.
- [ ] `rojo serve` arranca y el plugin de Rojo en Studio puede conectarse (comprobación manual del usuario si Codex no puede automatizarla).
- [ ] `Setup-Entorno.md` coincide con la realidad tras la ejecución.
- [ ] Si alguna herramienta falla o falta, se documenta en el informe qué no pudo verificarse.
- [ ] Todo el código escrito supera `stylua --check src tests` y `selene src`.

## Pruebas
Ejecutar los comandos anteriores y adjuntar la salida en el informe.

## Restricciones
No instalar software sin autorización; no añadir dependencias externas (Wally, etc.) ni lógica de juego; no tocar `docs/` salvo el archivo indicado y la excepción siguiente.

**Excepción documental (solo durante la ejecución autorizada de esta tarea, y únicamente para registrarla según [[AGENTS]]):** Codex puede actualizar (1) el estado de esta tarea y su «Informe final», (2) `docs/04-Arquitectura/Setup-Entorno.md` (el archivo ya indicado), (3) `docs/07-Registro/PROGRESS.md`, (4) la nota de entrega `docs/07-Registro/Entregas/ENT-TASK-001.md` y (5) los registros de pruebas o errores estrictamente necesarios en `docs/07-Registro/Pruebas/` y `docs/07-Registro/Errores/`. Cualquier otra modificación de `docs/` sigue prohibida. Esta excepción no cambia el objetivo, los requisitos, las dependencias, los criterios de aceptación ni el alcance.

## Entregable
Estructura de proyecto + configs + `Setup-Entorno.md` en una rama `codex/task-001-scaffold`.

## Informe final
(Formato de [[AGENTS]]: qué se hizo · archivos · pruebas · criterios ✔/✘ · problemas · siguiente paso.)

## Bloqueos / preguntas
—
