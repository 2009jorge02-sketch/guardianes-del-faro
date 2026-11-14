---
tipo: prueba
tarea: TASK-001
fecha: "2026-11-14"
plataforma: Claude Code (lectura de archivos, sin MCP)
resultado: correcta
---
# Prueba: lectura mínima para TASK-001

**Objetivo:** comprobar qué documentos hay que leer realmente para ejecutar [[TASK-001]] con el protocolo de [[INDICE-IA]], sin perder requisitos ni criterios.

## Lectura necesaria (tamaños medidos en bytes)
| Orden | Documento | Qué se lee | Bytes |
|---|---|---|---|
| 1 | `AGENTS.md` | completo (se carga siempre) | 4 694 |
| 2 | [[INDICE-IA]] | completo | 5 731 |
| 3 | [[TASK-001]] | **completa** (regla obligatoria) | 3 706 |
| 4 | [[ADR-002-herramientas]] | §Decisión y §Actualización (citado para Luau CLI y Rojo) | 637 |
| 5 | [[ARCHITECTURE]] | §Estructura del repositorio (requisito 1 y 2) | 1 197 |
| 6 | [[Setup-Entorno]] | completo (el requisito 6 pide revisarlo entero) | 2 780 |
| — | Dependencias | `depende_de: []`: ninguna que consultar | 0 |
| — | `PROGRESS.md` | solo últimas líneas | ≈ 2 600 |
| — | `ENTREGA-PARA-CODEX.md` | solo en la primera sesión de Codex | 6 146 |

Sesión normal: ≈ 21 300 B; primera sesión: ≈ 27 500 B.

## Protocolo anterior (referencia)
Leer `AGENTS.md` (antiguo, 5 044), `ENTREGA-PARA-CODEX` (6 146), `PROGRESS` (4 489), la tarea (3 706) y los tres documentos enlazados completos (2 097 + 4 280 + 2 780): **28 542 B** en cada sesión.

## Resultado
- Medido: ahorro de ≈ 25 % de bytes en una sesión normal (≈ 7 200 B) y ≈ 4 % en la primera sesión; el resto es lectura obligatoria.
- No se omitió ningún requisito ni criterio: la tarea se lee entera y las secciones omitidas de los documentos enlazados no están citadas por ella.
- Estimación (no medida): 1 token ≈ 3,5–4 bytes de texto en español, es decir, unos 1 800–2 000 tokens ahorrados por sesión. No se midieron tokens reales.
- **MCP:** comprobado después en Claude Code con `get_note_properties` (propiedades de TASK-001), `get_vault_file_partial` (solo §Decisión de ADR-002, ~290 B) y `search_vault_simple` (`rojo build`, 2 archivos); no se probó en Codex.
