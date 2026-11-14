---
id: ADR-002
titulo: Herramientas de desarrollo (Rojo, StyLua, Selene, luau-lsp)
estado: aceptada e instalada (Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0 vía Rokit 1.2.0); luau-lsp y Luau CLI pendientes
fecha: 2026-11-14
decide: "Claude (instalación: usuario)"
---
# ADR-002 · Herramientas

## Contexto
Codex trabaja con **archivos en Git**, no dentro de Studio. Versiones consultadas el 2026-11-14 ([[Politicas-y-Limites]]): Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0, luau-lsp 1.70.1. Roblox Studio ofrece MCP integrado (compatibilidad con Codex **[PV]**).

## Opciones
| Herramienta | Beneficio | Coste/complejidad | Recomendación |
|---|---|---|---|
| **Rojo** | Sincroniza `src/` ↔ Studio; **imprescindible** para flujo Git+Codex | Plugin en Studio + CLI | **Adoptar (MVP)** |
| **StyLua** | Formato automático consistente | CLI, config mínima | **Adoptar** |
| **Selene** | Lint (errores comunes, globales) | CLI; `selene.toml` con stdlib Roblox | **Adoptar** |
| luau-lsp | Tipos y diagnóstico en editor; analiza `--!strict` | Requiere sourcemap de Rojo | Opcional (recomendado cuando haya código) |
| Gestor (Rokit/Aftman) | Versiones fijadas del equipo | Un paso más | Recomendado (Rokit) si el usuario lo acepta |
| MCP de Studio | Playtest/inspección desde agente | Compatibilidad Codex **[PV]** | Evaluar en Alfa |

## Decisión
Rojo + StyLua + Selene (+ luau-lsp opcional) con `rokit.toml`. **No se instala nada sin autorización del usuario**; [[TASK-001]] solo crea los archivos de configuración y documenta cómo instalar. Windows: Git y las herramientas deben estar en el PATH ([[Como-trabajamos]]).

## Actualización 2026-11-14
Con autorización expresa del usuario se instalaron Rojo, StyLua y Selene con Rokit y el plugin de Rojo; resultados en [[Setup-Entorno]]. Sigue **pendiente** un ejecutor de pruebas Luau fuera de Studio (Luau CLI): no instalado; Codex puede proponerlo en [[TASK-001]] y se necesita autorización. luau-lsp: opcional.

## Consecuencias
Entorno listo; la conexión Studio↔Rojo debe confirmarla el usuario la primera vez ([[Setup-Entorno]]).
