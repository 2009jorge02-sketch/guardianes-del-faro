---
tipo: arquitectura
tema: Entorno de desarrollo (Windows)
verificado: 2026-11-14 (comandos ejecutados por Claude)
---
# Entorno de desarrollo

Decisión: [[ADR-002-herramientas]]. Tarea que lo consume: [[TASK-001]].

## Estado verificado (2026-11-14)
| Herramienta | Versión | Comprobación |
|---|---|---|
| Git | 2.56.1.windows.1 | `git --version`; repo en esta carpeta con 1 commit inicial; remoto `origin` en GitHub: ver [[Estado-de-Conexiones]] §GitHub |
| Rokit | 1.2.0 | `rokit --version`; `rokit list` muestra las 3 herramientas |
| Rojo | 7.7.1 | `rojo --version`; `rojo build` sobre un proyecto de prueba temporal terminó bien |
| StyLua | 2.6.0 | `stylua --check` sobre un archivo de prueba: exit 0 |
| Selene | 0.32.0 | `selene` sobre un archivo de prueba: 0 errores |
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
```

## Conectar Studio con Rojo (manual, una vez)
1. Abre Roblox Studio (reinícialo si estaba abierto al instalar el plugin) → pestaña **Plugins** → botón **Rojo**.
2. Ejecuta `rojo serve` en el repo → en el plugin pulsa **Connect**.
Si el botón no aparece, el plugin no se cargó: reinicia Studio y repite `rojo plugin install`.

## Configuración existente
`stylua.toml` (Luau, tabs, ancho 100, LF), `selene.toml` (std `roblox`), `.luaurc` (strict), `.gitattributes` (LF en `.luau`).

## Pendiente
- **Luau CLI** (para pruebas fuera de Studio): no instalado; requiere decisión ([[ADR-002-herramientas]]).
- luau-lsp: opcional; no instalado.
- Commits y push: solo cuando el usuario lo pida. Estado real del remoto en [[Estado-de-Conexiones]] §GitHub.
