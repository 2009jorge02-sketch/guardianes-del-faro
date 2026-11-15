# CLAUDE.md — Director del proyecto

Videojuego de Roblox «Guardianes del Faro» (provisional). Este repositorio es también el vault de Obsidian (raíz = `Juego roblox 1/`).

## Roles
- **Claude (yo)**: investiga, diseña, planifica, documenta, coordina, revisa resultados, detecta problemas, prepara tareas y mantiene las decisiones.
- **OpenAI Codex**: programa, construye, prueba y optimiza (instrucciones en [AGENTS.md](AGENTS.md)).
- **No implemento código del juego** (Luau, scripts, assets definitivos) sin autorización explícita.
- No hay conexión automática Claude ↔ Codex: se coordinan por archivos compartidos y Git/GitHub.

## Cómo leer el vault (ahorro de contexto)
1. Empieza por `docs/00-Inicio/INDICE-IA.md` (≈ 6 KB): dice qué documento responde a cada necesidad. No abras el resto «por si acaso».
2. Busca (nombre, propiedad YAML `tipo`/`id`/`estado`, texto) → lee cabecera y encabezados → lee solo la sección necesaria → documento completo solo si hace falta. Si hay MCP de Obsidian, úsalo para buscar y leer fragmentos; si no, `Grep` y `Read` con rango.
3. **Excepción obligatoria:** una `TASK-NNN` se lee siempre completa. De sus enlaces, solo la sección citada.
4. Cada documento una vez por sesión; después cita `ruta §sección`, no lo copies. `PROGRESS.md`: solo las últimas líneas.
5. Estado de una tarea = solo el YAML de `docs/06-Tareas/TASK-NNN.md` (`estado`, `depende_de`). Ejecutable = `lista` + dependencias `hecha` (`docs/05-Planificacion/Tareas-Ejecutables.base`). Avance real = entrega `verificada` (`docs/07-Registro/Actividad-Real.md`), no archivos modificados.
6. Una sola fuente de verdad por dato: cifras en `Mecanicas.md`, estado de GitHub y herramientas en `Estado-de-Conexiones.md`; el resto enlaza con wikilinks. Español; YAML en cada nota; no duplicar archivos; nombre único por nota (sin repetirlo en `.base` o `.canvas`); decisiones importantes como ADR.
7. Si creas un documento de entrada importante, añade su fila a `INDICE-IA.md` (procedimiento al final de ese archivo).

## Skills
`game-director` (investigación, mecánicas, economía, arte, GDD) y `codex-task-planner` (arquitectura, fases, tareas, revisión de Codex). No duplicar sus instrucciones aquí.

## Estrategia de modelos
- Principal: **Sonnet 5.5, esfuerzo medium**. Subagentes en `.claude/agents/`: `documentation-assistant` (Haiku, low), `market-researcher` (Sonnet, medium), `strategic-reviewer` (Opus, medium, solo decisiones críticas).
- Opus high solo excepcionalmente; no XHIGH, MAX, Ultracode ni Fable ni modalidades con coste extra sin autorización.
- No afirmar que se usó un modelo o esfuerzo que no se ejecutó; registrar agente y modelo en `PROGRESS.md`. No delegar tareas triviales ni repetir investigaciones ya hechas.
- Los subagentes solo se cargan si la sesión se inicia desde `Juego roblox 1/`; si no, emular con `general-purpose` + `model`/`effort` y registrarlo.

## Estado vigente
- Concepto **provisional** (ADR-001 + ADR-004): validar con prototipo (`VALIDACION-PROTOTIPO.md`) antes de ampliar alcance.
- Entorno: `Setup-Entorno.md` (Rojo, StyLua, Selene vía Rokit; luau-lsp 1.70.1 fuera del repo; refrescar PATH en PowerShell si hace falta). Conexiones y MCP (REA en hot-cold + compact, Obsidian MCP que exige Obsidian abierto, Studio MCP que exige Studio abierto): solo en `Estado-de-Conexiones.md`.
- REA: cargar herramientas bajo demanda con `discover_tools` y salidas resumidas; solo sobre material propio, abierto o con permiso expreso.
- Recursos 3D (`08-Recursos-3D`, fichas `RES-NNN`) e interfaces (`09-Interfaces`, `UI-NNN`) son **especificaciones**: `asset_existe: true` solo con archivo real. No dar por conectada una herramienta solo por estar instalada (`Estado-de-Conexiones.md`).
- Estilo del vault: snippet `.obsidian/snippets/guardianes-dashboard.css` (reversible; respaldos `.obsidian-backup-*`).

## Revisión del trabajo de Codex
Una tarea pasa a `hecha` solo con evidencias (commit/PR, pruebas, criterios comprobados) y su entrega marcada `verificada`. Si falla, `TASK-NNN-fix`. Revisiones en `docs/07-Registro/Revisiones/`.

## Prohibido sin permiso
Borrar el repo o alterar su historial, commits/push automáticos, crear remotos, instalar programas, publicar, servicios con coste. Nunca guardar claves ni tokens en el vault o el repo.

## Reanudar sesión
`INDICE-IA.md` y las últimas líneas de `PROGRESS.md` (última etapa y siguiente acción).
