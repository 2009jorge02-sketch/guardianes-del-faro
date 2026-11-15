# Herramientas del MCP integrado de Roblox Studio

Fuente: documentación oficial de Roblox leída el 2026-11-15 (https://create.roblox.com/docs/studio/mcp). Los nombres pueden cambiar con las versiones de Studio: comprueba la lista real que ofrezca la sesión antes de usarlos. Cada llamada necesita `studio_id` (obtenlo con `list_roblox_studios`).

| Grupo | Herramientas | Impacto |
|---|---|---|
| Estado y consola | `list_roblox_studios`, `get_studio_state`, `get_console_output`, `screen_capture` | lectura |
| Árbol de datos | `search_game_tree`, `inspect_instance`, `subagent` | lectura |
| Scripts | `script_read`, `script_search`, `script_grep`, `multi_edit` | lectura; `multi_edit` **modifica** |
| Luau | `execute_luau` (`datamodel_type`: Edit, Client o Server) | **ejecuta código arbitrario** en el lugar abierto |
| Playtest | `start_stop_play` | arranca/para una sesión |
| Entrada simulada | `character_navigation`, `user_keyboard_input`, `user_mouse_input` | actúa sobre la sesión |
| Recursos | `search_asset`, `insert_asset`, `upload_image`, `store_image` | `insert_asset` modifica; subir imágenes afecta a servicios externos |
| Generación | `generate_mesh`, `generate_material`, `generate_animation`, `generate_procedural_model`, `generate_avatar`, `wait_job_finished` | **puede consumir cuota o créditos**: solo con autorización expresa |
| Otros | `http_get`, `skill`, `save_place`, `submit_feedback` | `save_place` modifica; `http_get` es externo |

Seguridad (palabras de la propia documentación): los clientes MCP pueden leer y modificar el contenido de los lugares abiertos; conecta solo clientes de confianza.
