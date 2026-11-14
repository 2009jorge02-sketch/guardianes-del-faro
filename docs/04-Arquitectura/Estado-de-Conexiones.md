---
tipo: arquitectura
tema: Conexiones y herramientas accesibles desde la sesión de Claude
verificado: 2026-11-14
---
# Estado de conexiones (verificado 2026-11-14)

«Instalado en Windows» no significa «accesible para Claude». Esta es la **fuente única** de este estado; otros documentos enlazan aquí en lugar de repetirlo.

## GitHub (comprobado con Git)
- Remoto `origin` configurado (fetch y push): `https://github.com/2009jorge02-sketch/guardianes-del-faro.git`.
- Rama local `main` sigue a `origin/main`; ambas en el commit inicial `d1c733c` («Initial commit»). Comprobado con `git remote -v`, `git branch -vv` y `git ls-remote --heads origin` (solo lectura).
- Todo el trabajo posterior (docs, configuración, `CLAUDE.md`, `AGENTS.md`, etc.) está **sin commit** en el disco local y por tanto **no está en GitHub**.
- Nadie hace commits ni push automáticos: Obsidian Git con intervalos a 0 y push desactivado; Claude no los hace sin petición expresa.
- No verificado: visibilidad del repositorio (pública o privada) y credenciales de push.

## Resto de herramientas
| Herramienta | Resultado | Notas |
|---|---|---|
| Git | Accesible por terminal | Ver sección GitHub. Versión en [[Setup-Entorno]]. |
| Rokit / Rojo / StyLua / Selene | En el PATH de usuario (`.rokit\bin`) | Versiones en [[Setup-Entorno]]; no se ejecutaron en esta misión. |
| Figma | **Conector autenticado** | Ver [[Figma]]. Sin archivo del proyecto. |
| Blender | Instalado (Blender 5.3), **sin conexión con Claude** | Ver [[Blender]]. |
| Waspes 3D | **No accesible** | Ver [[Waspes-3D]]. Sin créditos gastados. |
| Roblox Open Cloud | **No accesible** | Sin claves ni permisos creados. |
| Roblox Studio | No verificado | Sin herramienta de control desde Claude. |
| Codex | Existe configuración local en el PC; **sin comunicación directa** | Coordinación solo por archivos y Git ([[Flujo-Claude-Codex]]). |
| Obsidian | Instalado (1.15.1) | Claude no puede abrir ni manejar la interfaz: solo valida archivos; la comprobación visual la hace el usuario. |
| Obsidian Git | Instalado y activado en el vault correcto | Ajustes seguros: sin auto-commit, auto-pull ni auto-push. |
| Excalidraw | Instalado y activado en el vault correcto | Copiado desde el `.obsidian` de la carpeta superior. |

## Configuración activa de Obsidian
La carpeta activa es `Juego roblox 1/.obsidian/` (CSS en `snippets/`, `graph.json`, `core-plugins.json` con Bases activado, y los plugins Git y Excalidraw). El `.obsidian` de `juego roblox1/` es el antiguo y `Juego roblox 1/.obsidian.zip` es solo un archivo comprimido de copia, no una carpeta activa. Respaldos: `.obsidian-backup-*`.

- Obsidian MCP (comprobado 2026-11-14, sesión reiniciada): conector `obsidian_juego_roblox_1` operativo en Claude Code (servidor v3.3.0, HTTP local). Verificado en solo lectura: propiedades de una nota, lectura de una sección y búsqueda de texto. Codex: entrada registrada en su `config.toml`, **sin probar**.
