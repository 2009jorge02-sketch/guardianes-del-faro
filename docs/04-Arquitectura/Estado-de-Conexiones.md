---
tipo: arquitectura
tema: Conexiones y herramientas accesibles desde Claude y Codex
verificado: 2026-11-15
---
# Estado de conexiones (verificado 2026-11-15)

«Instalado en Windows» no significa «accesible para Claude». Esta es la **fuente única** de este estado; otros documentos enlazan aquí en lugar de repetirlo. Niveles: **instalado → registrado → conectado → probado**.

## GitHub (comprobado con Git)
- Remoto `origin` (fetch y push): `https://github.com/2009jorge02-sketch/guardianes-del-faro.git`. Repositorio **privado** y correctamente conectado (última comprobación: 2026-11-15): la API sin autenticar responde 404, y `git ls-remote`, `git fetch` y el push a `origin/main` con las credenciales del usuario funcionan.
- **Sincronización:** en la última comprobación (2026-11-15), `main` local y `origin/main` coincidían y el árbol de trabajo estaba limpio. **No se fija aquí ningún hash** (cambia con cada commit): el estado actual se consulta con `git status -sb`, `git rev-parse HEAD` y `git rev-parse origin/main`.
- Los cambios pendientes de commit o de push, si los hay, los muestra siempre `git status`; este documento no los lista.
- Nadie hace commits ni push automáticos: Obsidian Git con intervalos a 0 y push desactivado; Claude no los hace sin petición expresa.
- Seguridad: sin credenciales en archivos versionados ni en el historial (comprobado por patrones, sin mostrar valores). Los tokens del plugin MCP Connector viven en `.obsidian/plugins/mcp-tools-istefox/data.json`, **ignorado por Git**: no incluirlo en copias ni ZIP que se compartan. El log `diagnostic.log` del mismo plugin ya no se versiona.
- No verificado: permisos del repositorio de GitHub más allá de la visibilidad.

## MCP y herramientas de IA
| Elemento | Estado | Dependencias y notas |
|---|---|---|
| REA 6.9.0 (`rea`) en **Claude Code** | Registrado, conectado y probado (5 herramientas, `discover_tools`, invocación) | Perfil `hot-cold` + `compact`: catálogo inicial ≈ 16 KB frente a ≈ 4,7 MB. Tras `discover_tools` hay que repetir la búsqueda para cargar la herramienta. Sin motores externos (Ghidra, JADX…) |
| REA en **Codex** | Registrado, conectado y probado por el usuario | Catálogo completo (`full`) con esquemas `compact` (≈ 0,65 MB). `hot-cold` en Codex sin probar |
| Obsidian MCP (`obsidian_juego_roblox_1`) en Claude Code | Registrado; probado en lectura el 2026-11-14 | **Requiere Obsidian abierto con este vault** y que el cliente exponga sus herramientas: si Obsidian estaba cerrado al iniciar la sesión, hay que abrirlo y reiniciar el cliente |
| Obsidian MCP en Codex | Registrado y probado por el usuario | Mismas dependencias |
| MCP de Roblox Studio (`Roblox_Studio`) en Codex | Registrado; operativo según el usuario | **Requiere una instancia de Studio abierta** y «Enable Studio as MCP server». Claude Code no lo tiene configurado. Ver [[Roblox-Studio-MCP]] |
| `node_repl` en Codex | Registrado | No probado |
| Skills de Codex (`.agents/skills/`, 4) | Probadas por el usuario con `/skills` | Del repo; ver [[AGENTS]] |
| Subagentes de Claude (`.claude/agents/`, 3) | Archivos válidos | Solo se cargan si la sesión de Claude se inicia desde `Juego roblox 1/` |

## Herramientas de desarrollo
| Herramienta | Estado | Notas |
|---|---|---|
| Git | Probado | Ver GitHub arriba. Versión en [[Setup-Entorno]] |
| Rokit, Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0 | Instalados y probados (proyecto temporal, 2026-11-15) | En el PATH de usuario (`.rokit\bin`); necesitan `rokit.toml` |
| luau-lsp 1.70.1 | Instalado y probado | `C:\Users\tatia\tools\luau-lsp\` (fuera del repo, sin PATH). Requiere las definiciones de Roblox y el sourcemap de Rojo (ver [[Setup-Entorno]]) |
| Roblox Studio | Instalado; cerrado en la última comprobación | Plugins de Rojo y Waspes presentes. La conexión Rojo↔Studio la confirma el usuario la primera vez |
| Blender 5.3 | Instalado, **sin conexión con Claude** | Ver [[Blender]] |
| Waspes 3D | **No accesible** desde Claude | Ver [[Waspes-3D]]. Sin créditos gastados |
| Roblox Open Cloud | **No accesible** | Sin claves ni permisos creados |
| Figma | **Conector autenticado** | Ver [[Figma]]. Sin archivo del proyecto |
| Obsidian 1.15.1, Obsidian Git, Excalidraw | Instalados y activados en este vault | Git con ajustes seguros (sin auto-commit, auto-pull ni auto-push). Claude no puede manejar la interfaz: la comprobación visual la hace el usuario |

## Configuración activa de Obsidian
La carpeta activa es `Juego roblox 1/.obsidian/` (CSS en `snippets/`, `graph.json`, `core-plugins.json` con Bases activado, y los plugins Git, Excalidraw y MCP Connector). El `.obsidian` de `juego roblox1/` es el antiguo y `Juego roblox 1/.obsidian.zip` es solo un archivo comprimido de copia, no una carpeta activa. Respaldos: `.obsidian-backup-*` (ignorados por Git; sin credenciales).
