---
tipo: arquitectura
tema: Entorno de desarrollo (Windows)
verificado: 2026-11-15 (comandos ejecutados por Claude; toolchain probada en un proyecto temporal fuera del repo)
---
# Entorno de desarrollo

Decisión: [[ADR-002-herramientas]]. Tarea que lo consume: [[TASK-001]].

## Estado verificado (2026-11-15)
| Herramienta | Versión | Comprobación |
|---|---|---|
| Git | 2.56.1.windows.1 | `git --version`; remoto `origin` privado en GitHub: estado en [[Estado-de-Conexiones]] §GitHub |
| Rokit | 1.2.0 | `rokit --version`; necesita `rokit.toml` en la carpeta o en una superior |
| Rojo | 7.7.1 | `rojo build` y `rojo sourcemap` sobre un proyecto temporal: correctos |
| StyLua | 2.6.0 | `stylua --check` sobre un proyecto temporal con `stylua.toml` del repo: exit 0 |
| Selene | 0.32.0 | `selene src` con `selene.toml` del repo (std `roblox`): 0 errores. Sin ese archivo marca `game` como no definido |
| luau-lsp | 1.70.1 | Instalado **fuera del repo** en `C:\Users\tatia\tools\luau-lsp\` (no está en el PATH). `luau-lsp analyze` sin errores con las definiciones de Roblox y el sourcemap de Rojo |
| Plugin Rojo | `RojoManagedPlugin.rbxm` (504 KB) | copiado por `rojo plugin install` a `%LOCALAPPDATA%\Roblox\Plugins` (presencia del archivo verificada; **que cargue dentro de Studio no está verificado**) |
Versiones fijadas en `rokit.toml` (raíz del repo). Roblox Studio y Claude Desktop no se verificaron por línea de comandos.

## Reglas prácticas
- Rokit solo ejecuta Rojo/StyLua/Selene si hay un `rokit.toml` en la carpeta actual o en una superior. **Ejecuta los comandos dentro del repo.**
- Una terminal abierta **antes** de instalar Git/Rokit no verá el PATH nuevo: cierra y abre la terminal, o en PowerShell:
  `$env:Path = [Environment]::GetEnvironmentVariable('Path','Machine') + ';' + [Environment]::GetEnvironmentVariable('Path','User')`
- Si cambias de máquina: `rokit install` en la raíz restaura las versiones.

## Comandos habituales
```powershell
rokit install                  # instala/ajusta las herramientas de rokit.toml
rojo serve                     # sincroniza src/ con Studio (tras crear default.project.json en TASK-001)
rojo build -o build/Guardianes.rbxl
stylua src tests               # formatear
stylua --check src tests       # comprobar formato
selene src                     # lint
# Tipos con luau-lsp (necesita default.project.json): sourcemap de Rojo + definiciones de Roblox
rojo sourcemap default.project.json -o sourcemap.json
C:\Users\tatia\tools\luau-lsp\luau-lsp.exe analyze --definitions=C:\Users\tatia\tools\luau-lsp\globalTypes.None.d.luau --sourcemap=sourcemap.json src
```
Sin el sourcemap, luau-lsp da falsos errores con los servicios definidos en `default.project.json` (p. ej. `ReplicatedStorage.Shared`); sin las definiciones no entiende `game`. `sourcemap.json` ya está en `.gitignore`.

## Conectar Studio con Rojo (manual, una vez)
1. Abre Roblox Studio (reinícialo si estaba abierto al instalar el plugin) → pestaña **Plugins** → botón **Rojo**.
2. Ejecuta `rojo serve` en el repo → en el plugin pulsa **Connect**.
Si el botón no aparece, el plugin no se cargó: reinicia Studio y repite `rojo plugin install`.

## Configuración existente
`stylua.toml` (Luau, tabs, ancho 100, LF), `selene.toml` (std `roblox`), `.luaurc` (strict), `.gitattributes` (LF en `.luau`).

## Pendiente
- **Luau CLI** (para pruebas fuera de Studio): no instalado; requiere decisión ([[ADR-002-herramientas]]). luau-lsp comprueba tipos pero no ejecuta pruebas.
- Integrar luau-lsp en el repo (`rokit.toml`, scripts, criterio de cierre de tareas): pendiente de decisión; hoy es una comprobación recomendada, no obligatoria.
- MCP de Roblox Studio: ver [[Roblox-Studio-MCP]] (requiere una instancia de Studio abierta).
- Commits y push: solo cuando el usuario lo pida. Estado real del remoto en [[Estado-de-Conexiones]] §GitHub.
