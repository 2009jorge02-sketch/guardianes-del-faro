---
tipo: arquitectura
tema: Servidor MCP integrado de Roblox Studio (distinto de Rojo)
verificado: 2026-11-15
---
# Servidor MCP de Roblox Studio

## Qué es y en qué se diferencia de Rojo
| | Rojo (ya instalado) | MCP de Studio |
|---|---|---|
| Función | Sincroniza archivos del repo con Studio | Permite a un agente **leer y actuar** en un Studio abierto (consola, playtest, scripts, capturas) |
| Dirección | Archivos → Studio | Agente ↔ Studio |
| Doc. | [[Setup-Entorno]] · [[ADR-002-herramientas]] | Esta nota |
No se sustituyen: Rojo sigue siendo el camino para el código del juego.

## Estado verificado (2026-11-15)
- Según la documentación oficial de Roblox (Creator Hub, «Studio MCP server»), el servidor **viene integrado en Roblox Studio**. El repositorio antiguo `Roblox/studio-rust-mcp-server` está archivado; se recomienda el integrado.
- En este PC: existe `%LOCALAPPDATA%\Roblox\mcp.bat` y Studio está instalado.
- **Codex** tiene ya una entrada `Roblox_Studio` en su `config.toml` que lanza ese `.bat` con `cmd.exe`.
- **Claude Code**: no tiene este servidor configurado.
- **Verificado por el usuario con Codex (2026-11-15):** Codex reconoce las skills y conecta con el MCP de Studio. Resultado confirmado por el usuario; Claude no lo ha probado.

## Pasos para dejarlo operativo en Codex
1. Abre Roblox Studio (versión reciente) con el lugar del proyecto.
2. **Assistant → ⋯ → Manage MCP Servers → activa «Enable Studio as MCP server»**. Un indicador verde muestra clientes conectados.
3. En la misma pantalla, bajo *Quick connect*, activa **Codex CLI** (o el cliente que uses). Si no aparece, instálalo y reinicia Studio.
4. Reinicia Codex y Studio tras cualquier cambio de configuración.
5. Comprueba en Codex: debe listar las herramientas de `Roblox_Studio` (por ejemplo `list_roblox_studios`).
6. Alternativa manual (Windows), comando oficial: `cmd.exe /c %LOCALAPPDATA%\Roblox\mcp.bat`. La entrada de Codex ya equivale a ello.

## Permisos y seguridad
- Los clientes MCP pueden **leer y modificar** el contenido del lugar abierto: conecta solo clientes de confianza y abre un lugar de prueba mientras se prueba.
- Orden de uso: solo lectura primero; ejecutar Luau, editar scripts, insertar recursos o guardar requieren **autorización del usuario**; las herramientas `generate_*` pueden consumir cuota o créditos y requieren autorización expresa.
- No se han concedido permisos adicionales ni modificado proyectos de Studio al preparar esto.

## Quién lo usa
Skill `roblox-playtest-debugger` (pruebas y rendimiento) y, para recursos, `roblox-asset-pipeline`. Lista de herramientas: `.agents/skills/roblox-playtest-debugger/references/studio-mcp.md`. Estado general de conexiones: [[Estado-de-Conexiones]].
