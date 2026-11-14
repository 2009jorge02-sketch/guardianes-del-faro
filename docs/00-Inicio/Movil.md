---
tipo: guia
categoria: navegacion
actualizado: 2026-11-14
---
# Consulta desde el móvil (iPhone)

Estado: **solo preparado**. No se ha contratado ni configurado ninguna sincronización, y no se ha probado en la app móvil.

## Qué ya está pensado para móvil
- [[Home]] usa tarjetas en 2 columnas en pantallas estrechas (snippet `guardianes-dashboard`), tablas cortas y enlaces grandes.
- Los Canvas y el gráfico funcionan en la app móvil, pero son más cómodos en tableta/PC.
- Las Bases (Tareas, Recursos, Interfaces) funcionan en móvil si la app es reciente; con pantallas pequeñas muestra pocas columnas por vista.
- Si el snippet no cargase en el móvil, las notas siguen siendo legibles (callouts normales).

## Alternativas para llevar el vault al móvil (decidir más adelante)
| Opción | Ventaja | Riesgo |
|---|---|---|
| Obsidian Sync (de pago) | Integrado, resuelve conflictos | **No contratado**; coste |
| iCloud Drive (copia del vault) | Gratis, sin cuenta extra | En Windows, conflictos si dos dispositivos editan a la vez |
| Git (el repo ya tiene remoto) + app móvil con plugin Git | Historial y sin sobrescrituras silenciosas | Configuración manual y plugin en móvil; **requiere autorización** |
| Solo lectura (GitHub en el navegador) | Sin riesgo de sobrescribir | No se ven Bases, Canvas ni estilos |

## Recomendación prudente
1. Mantener el PC como única fuente de edición.
2. Para empezar, consultar por **solo lectura**; las ediciones móviles se añaden solo cuando se elija sincronización.
3. Si algún día se abre el vault en móvil: **no** mezclar dos sincronizadores a la vez, y mantener los respaldos (`.obsidian-backup-2026-11-14`).
4. La carpeta `.obsidian/` incluye plugins y snippets; los ajustes de apariencia móvil pueden diferir de los de escritorio.
