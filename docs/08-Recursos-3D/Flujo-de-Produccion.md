---
tipo: proceso
categoria: recursos-3d
actualizado: 2026-11-14
---
# Flujo de producción e integración de recursos 3D

Claude **especifica**; Codex **gestiona la creación técnica, integración y pruebas** (con el usuario donde haga falta abrir herramientas). No hay conexión automática entre ellos: todo pasa por la ficha `RES-NNN`, la tarea `TASK-NNN` y el repositorio ([[Flujo-Claude-Codex]]).

| # | Paso | Responsable | Qué se actualiza en la ficha |
|---|---|---|---|
| 1 | Identificar el recurso necesario (GDD, mapa, tarea) | Claude | — |
| 2 | Crear la ficha con la plantilla [[recurso-3d]] | Claude | `id`, `categoria`, `funcion`, `prioridad` |
| 3 | Definir aspecto y finalidad | Claude | sección «Descripción de diseño» |
| 4 | Preparar referencias (imágenes aprobadas, licencia clara) | Claude / usuario | `imagen_referencia` |
| 5 | Elegir herramienta aprobada: [[Blender]], [[Waspes-3D]] u otra | Claude propone, usuario aprueba | `herramienta` |
| 6 | Crear el modelo | Usuario / Codex (según herramienta) | `estado_produccion: en_produccion`, `archivo_fuente` |
| 7 | Revisar geometría y materiales | Claude (revisión) | observaciones |
| 8 | Optimizar para Roblox (presupuestos de [[Rendimiento]]) | Codex / usuario | `presupuesto`, `materiales_texturas` |
| 9 | Exportar en formato compatible (FBX/glTF según [[Politicas-y-Limites]]) | Codex / usuario | `archivo_exportado`, `formato`, `estado_produccion: listo` |
| 10 | Integrar en Roblox Studio (importación y/o Rojo) | Codex | `integracion_roblox: en_progreso` |
| 11 | Verificar funcionamiento y rendimiento | Codex | informe de la tarea; prueba en [[Pruebas-y-Errores]] |
| 12 | Registrar el resultado en Obsidian y revisar | Codex → Claude | `integracion_roblox: integrado`, `asset_existe: true` |

## Estados
- `estado_produccion`: `pendiente` → `en_produccion` → `listo`.
- `integracion_roblox`: `pendiente` → `en_progreso` → `integrado`.
- `asset_existe` pasa a `true` solo cuando hay un archivo real exportado.
- Una ficha nunca se marca `listo` ni `integrado` sin evidencia (ruta del archivo, prueba o captura descrita).

## Reglas
- Para integrar un recurso, el trabajo debe existir como tarea en `docs/06-Tareas/` y enlazarse en `tarea_codex`.
- No generar ni descargar modelos, ni gastar créditos de servicios 3D, sin autorización del usuario ([[Waspes-3D]]).
- Los binarios se tratan según [[Estructura-de-Archivos]].
- Licencias: usar solo material con licencia verificada (riesgo R8 en [[Riesgos]]).
