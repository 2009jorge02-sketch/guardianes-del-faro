---
tipo: registro
actualizado: 2026-11-15
etapa_actual: "F completada; preparación previa al desarrollo (el desarrollo empieza el 2026-11-17)"
---
# Registro de progreso

> Reanudar aquí: ver el último **«Punto de reanudación»** al final de la bitácora (el más reciente es el del 2026-11-15). La lectura de este archivo debe limitarse a sus últimas líneas.

## Uso de modelos y agentes (registro verídico)

| Etapa | Trabajo | Agente / modelo realmente usado | Limitaciones |
|---|---|---|---|
| A | Estructura, CLAUDE.md, AGENTS.md, subagentes | Conversación principal: Sonnet 5.5 (medium) | Los archivos de `.claude/agents/` se crearon, pero **no se registran hasta reiniciar Claude Code** (error «Agent type not found»). |
| A | Plantillas Obsidian | Subagente `general-purpose` con `model: haiku`, `effort: low` (equivalente a `documentation-assistant`) | Sustituto del agente registrado. |
| B | Investigación de mercado y de políticas | Subagentes `general-purpose` con `model: sonnet`, `effort: medium` (equivalente a `market-researcher`) | Igual que arriba. |
| 2026-11-15 | Preparación previa al desarrollo | Conversación principal Sonnet 5.5 (el esfuerzo no se pudo verificar desde la sesión); agente `web-fetch` solo para leer documentación oficial; sin Haiku ni Opus | — |

*Nota 2026-11-15:* la limitación de la fila A describe lo ocurrido el 2026-11-14. Hoy los subagentes de `.claude/agents/` **solo se cargan si la sesión de Claude Code se inicia desde `Juego roblox 1/`** ([[Como-trabajamos]]).

## Entorno
- **Git:** instalado (2.56.1) y operativo. El 2026-11-14 no estaba en el PATH de la terminal de Claude hasta refrescarlo (ver [[Como-trabajamos]] §Git). Repositorio privado en GitHub, `main` sincronizada: estado actual en [[Estado-de-Conexiones]] (fuente única).
- **Vault:** `Juego roblox 1/`, creado a partir de `juego roblox1/.obsidian/` (original conservado). Desde el 2026-11-14 están **activados** Obsidian Git (ajustes seguros: sin auto-commit, auto-pull ni auto-push; push desactivado), Excalidraw y MCP Connector.
- **Herramientas:** Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0 (Rokit 1.2.0), luau-lsp 1.70.1 y REA 6.9.0; detalle en [[Setup-Entorno]] y [[Estado-de-Conexiones]].
- *Texto anterior (2026-11-14, histórico):* «Git no estaba en el PATH» y «Obsidian Git presente pero desactivado»; ya no es el estado vigente.

## Bitácora
- 2026-11-14 · Etapa A completada: carpetas, `.gitignore`, `templates.json`, 3 agentes, CLAUDE.md, AGENTS.md.
- 2026-11-14 · Etapa B: investigación (Sonnet medium ×2) → `02-Investigacion/`; 12 conceptos y matriz ponderada, escritos por la conversación principal (Sonnet medium).
- 2026-11-14 · Etapa C: revisión de finalistas con `model=opus`, `effort=medium` (agente general-purpose, no el registrado). Elegido Guardianes del Faro modificado → [[ADR-001-concepto]].
- 2026-11-14 · Etapa D: GDD y diseño (principal, Sonnet medium). Etapa E: arquitectura, ADR-002/003, roadmap, 12 tareas (TASK-001…012). Etapa F: auditoría → [[Auditoria-2026-11-14]].
- **Última etapa completada: F. Siguiente acción: el usuario aprueba concepto, instala Git/herramientas y lanza Codex con [[ENTREGA-PARA-CODEX]] (TASK-001).**
- 2026-11-14 · **Misión final:** Git 2.56.1 y Rokit 1.2.0 verificados (hacía falta refrescar el PATH de la terminal de Claude). `rokit init` + add/install → Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0; `rojo plugin install` copió `RojoManagedPlugin.rbxm`; pruebas en carpeta temporal OK. Creados `stylua.toml`, `selene.toml`, `.luaurc`; `.gitattributes` y `.gitignore` ampliados. Obsidian Git habilitado con ajustes seguros (sin automatismos). Concepto revisado (principal Sonnet medium, skill game-director) → [[Revision-Concepto]], [[VALIDACION-PROTOTIPO]], [[ADR-004-validacion-concepto]]. Tareas 001/002/004/006/008/012 ajustadas; [[ENTREGA-PARA-CODEX]] v2.
- **Subagentes (misión final):** `Agent` con `documentation-assistant` sigue devolviendo «not found». Causa probable: Claude Code solo carga el primer `.claude/agents/` tras reiniciar, y esta sesión se inició en `juego roblox1/`, no en `Juego roblox 1/`. Frontmatter validado contra la documentación oficial (`name`, `description`, `tools`, `model`, `effort` son válidos) mediante el agente `claude-code-guide` (Sonnet por defecto, lectura de docs). No se usaron Haiku ni Opus en esta misión.
- Haiku solo se usó realmente para las 4 plantillas; el resto de la documentación mecánica la escribió la conversación principal porque delegar costaba más que hacerlo.

- 2026-11-14 · **Mejora del vault (Sonnet 5.5, sin subagentes; el nivel de esfuerzo no se pudo verificar desde la sesión):** [[Home]] rediseñado con vistas Bases; snippet CSS `guardianes-dashboard`; `graph.json` con colores por carpeta; propiedades `tipo` y `fecha_actualizacion` en TASK-001…012 (estados intactos); Bases de tareas, registro, decisiones, errores, pruebas, recursos 3D e interfaces; [[Catalogo-3D]] (21 fichas, ninguna con modelo real); [[Interfaces]] (7 fichas, sin diseño en [[Figma]]); 5 Canvas; [[Centro-de-Control]]; [[Estado-de-Conexiones]]. Respaldo: `.obsidian-backup-2026-11-14/`. Sin commits ni push.

- 2026-11-14 · **Optimización funcional:** Home reducido a próxima tarea ejecutable, en curso, revisión y bloqueos + 6 accesos; [[Tareas-Ejecutables.base]] separa tareas ejecutables de las documentadas; [[Actividad-Real]] y plantilla [[entrega]] para avances verificados; Canvas y Base duplicados renombrados (`Mapa-Flujo-Claude-Codex.canvas`, `Tabla-Interfaces.base`); estado de GitHub unificado en [[Estado-de-Conexiones]]. Sin commits ni push.

- 2026-11-15 · **Preparación previa al desarrollo** (sin programar el juego; sin commit ni push):
  - **REA 6.9.0** instalado con el procedimiento oficial de npm y verificado en Claude Code y Codex. Claude Code: catálogo `hot-cold` + esquemas `compact` (≈ 16 KB frente a ≈ 4,7 MB); Codex: catálogo completo (`full`) + `compact` (≈ 0,65 MB). Solo motores integrados; Ghidra, JDK, JADX e ILSpy no se instalaron a propósito.
  - **luau-lsp 1.70.1** instalado fuera del repo y probado junto a Rojo 7.7.1, StyLua 2.6.0 y Selene 0.32.0 en un proyecto temporal; necesita las definiciones de Roblox y `rojo sourcemap` ([[Setup-Entorno]]).
  - **GitHub** privado y `main` sincronizada con `origin/main` en `fdd006d` (commit del usuario). **Skills y subagentes:** 4 skills de Codex en `.agents/skills/` (verificadas por el usuario) y 3 subagentes de Claude válidos (solo se cargan si la sesión empieza en `Juego roblox 1/`); MCP de Roblox Studio operativo en Codex (requiere Studio abierto).
  - **Prompt de inicio de Codex** optimizado: lectura obligatoria de ≈ 88 KB en 29 archivos a ≈ 18 KB en 4 (AGENTS, INDICE-IA, la tarea y el final de este archivo) más las secciones citadas (bytes medidos; tokens estimados).
  - **Git:** `diagnostic.log` del plugin MCP Connector dejado de rastrear (`.gitignore` y `git rm --cached`; el archivo físico se conserva y sigue en el historial de `fdd006d`, sin secretos). Sin credenciales en archivos versionados ni en el historial.
  - **Consolidación documental:** `AGENTS.md`, `CLAUDE.md`, `ENTREGA-PARA-CODEX`, `Setup-Entorno`, `Estado-de-Conexiones`, `ADR-002` y `Como-trabajamos` actualizados; protocolo en [[Flujo-Claude-Codex]] y plantilla `tarea` con puntos de control; [[TASK-001]] aclara qué documentos puede actualizar Codex al ejecutarla. Las 12 tareas conservan sus estados y dependencias.
- **Punto de reanudación (2026-11-17):** 1) abrir Obsidian y Claude Code en `Juego roblox 1/`; 2) verificar las conexiones listadas en [[Estado-de-Conexiones]] y `git status`; 3) comenzar [[TASK-001]] **únicamente con autorización expresa del usuario**. Hasta entonces el juego no se desarrolla.
