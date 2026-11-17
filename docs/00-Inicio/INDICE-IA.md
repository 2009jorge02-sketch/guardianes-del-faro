---
tipo: indice-ia
actualizado: 2026-11-17
---
# Índice para IA (ligero)

Punto de entrada de Claude y Codex. **No lo copies en tus respuestas**: úsalo para decidir qué leer.

## Lectura progresiva (en este orden, parar en cuanto tengas lo necesario)
1. **Índice** (este archivo).
2. **Búsqueda**: por nombre, por propiedad YAML (`tipo`, `id`, `estado`, `tarea_codex`…) o por texto; no abras nada todavía.
3. **Cabecera**: solo el YAML y los encabezados de la nota candidata.
4. **Fragmento**: la sección necesaria (por encabezado o rango de líneas).
5. **Documento completo**: solo si el fragmento no basta, o si es una tarea (regla siguiente).

## Reglas fijas
- **Tarea `TASK-NNN`: leerla SIEMPRE completa** (objetivo, requisitos, dependencias, criterios de aceptación, pruebas, restricciones). Es la única lectura obligatoria entera.
- **Dependencias**: comprobar solo el `estado` (YAML) de cada tarea de `depende_de`; ejecutable = `lista` y todas `hecha` ([[Tareas-Ejecutables.base]]).
- **Enlaces de la tarea** (`Contexto`, `Requisitos`, `Restricciones`): leer solo la sección que cita cada enlace, no la nota entera.
- **Cada documento se lee una vez por sesión**; después, citar `ruta §sección` en lugar de copiar texto.
- [[PROGRESS]]: leer solo las últimas líneas de la bitácora. [[ENTREGA-PARA-CODEX]]: solo la primera sesión de Codex.
- Cifras de balance: solo en [[Mecanicas]]; arquitectura y carpetas: [[ARCHITECTURE]]; comandos y herramientas: [[Setup-Entorno]].
- Estados y fechas: siempre desde el YAML, nunca desde tablas de resumen.

## Necesito… → leo…
| Necesito | Lectura |
|---|---|
| Qué tarea toca ahora | [[Tareas-Ejecutables.base]] (vista «Proxima ejecutable») y luego la `TASK-NNN` |
| Visión general del juego | [[GDD]] (3 KB; remite al resto) |
| Cifras de enemigos, linterna, noches, cartas | [[Mecanicas]] por sección |
| Progresión, economía, monetización | [[Progresion-Economia]] · [[Monetizacion]] |
| Objetivo económico, previsión, adquisición, decisiones comerciales abiertas | [[Modelo-Economico]] · [[Adquisicion-Organica]] · [[Decisiones-Monetizacion-Pendientes]] · [[ADR-005-estrategia-comercial]] |
| Contrato de producto V4.1: cartas por monedas o Robux, recursos, derribo, votación de cartas, gates Q1–Q4, T00–T21 ↔ TASK | [[ADR-006-contrato-producto-v4]] |
| Política de revisión V4.2: autorrevisión por tarea, 4 auditorías por hito, modelos de menor coste | [[ADR-007-revision-por-hitos]] |
| Gates Q1–Q4: plan de playtest, consentimiento y fichas de evidencia | [[PLAYTEST_PLAN]] · [[Protocolo-Gates-Q]] |
| Guía estética: 12 referencias visuales (4 maestras + 8 de producción) | [[Indice-Referencias-Visuales]] |
| Mapa e isla | [[Mapas]] |
| Arte, UI, audio | [[Arte-UI-Audio]] |
| Arquitectura, carpetas Luau, módulos | [[ARCHITECTURE]] · [[Cliente-Servidor]] |
| Seguridad de remotos, rendimiento | [[Seguridad]] · [[Rendimiento]] |
| Herramientas, comandos, Git/GitHub | [[Setup-Entorno]] · [[Estado-de-Conexiones]] · [[Roblox-Studio-MCP]] (MCP de Studio, distinto de Rojo) |
| Por qué se decidió algo | ADR en [[Decisiones.base]] (leer solo el ADR citado) |
| Riesgos, fases, puertas de calidad | [[Riesgos]] · [[ROADMAP]] · [[MVP]] · [[VALIDACION-PROTOTIPO]] |
| Un recurso 3D | [[Catalogo-3D]] → ficha `RES-NNN` |
| Una pantalla | [[Interfaces]] → ficha `UI-NNN` |
| Errores, pruebas, avances verificados | [[Pruebas-y-Errores]] · [[Actividad-Real]] |
| Cómo coordinarse Claude ↔ Codex | [[Flujo-Claude-Codex]] · [[Centro-de-Control]] |

## Mapa de carpetas (`docs/`)
| Carpeta | Contenido | Entrada |
|---|---|---|
| `00-Inicio` | Panel, guías, glosario, este índice | [[Home]] |
| `01-Vision` | [[Concepto]] · [[Pilares]] · [[Publico-objetivo]] | [[Concepto]] |
| `02-Investigacion` | Mercado, competidores, ideas, políticas (terminada; no repetir) | [[Investigacion-Indice]] |
| `03-Diseno` | GDD, mecánicas, mapas, arte, economía, 3 Canvas de diseño | [[GDD]] · [[Enemigos]] |
| `04-Arquitectura` | Cliente/servidor, seguridad, rendimiento, entorno, conexiones, Canvas | [[ARCHITECTURE]] |
| `05-Planificacion` | Roadmap, MVP, riesgos, tareas (resumen y Bases) | [[TASKS]] · [[Tareas.base]] |
| `06-Tareas` | `TASK-001…012` (fuente de verdad del estado) | [[Tareas.base]] |
| `07-Registro` | PROGRESS, ADR, revisiones, entregas, errores, pruebas | [[Actividad-Real]] |
| `08-Recursos-3D` | 21 fichas `RES-NNN`, flujo, Blender, Waspes | [[Catalogo-3D]] |
| `09-Interfaces` | 7 fichas `UI-NNN`, Figma, especificación para Codex | [[Interfaces]] |
| `10-Coordinacion` | Centro de control y flujo Claude ↔ Codex | [[Centro-de-Control]] |
| `.agents/skills` (raíz del repo) | 4 skills de Codex: `roblox-luau-engineer`, `roblox-playtest-debugger`, `roblox-asset-pipeline`, `roblox-ui-implementation` | — |
| `_plantillas` | `tarea`, `decision`, `investigacion`, `revision`, `recurso-3d`, `interfaz`, `error`, `prueba`, `entrega` | — |

## Relaciones principales (para saltar sin cargar la red)
- [[GDD]] → [[Mecanicas]] · [[Progresion-Economia]] · [[Mapas]] · [[Arte-UI-Audio]] · [[Experiencia-Jugador]].
- [[Mecanicas]] → `Config` de [[TASK-002]]; enemigos → [[Enemigos]] → [[ADR-003-enemigos]] → [[TASK-005]].
- [[ADR-002-herramientas]] + [[Setup-Entorno]] → [[TASK-001]]. [[Mapas]] → [[TASK-003]] y [[RES-003-Isla-del-Faro]].
- [[Arte-UI-Audio]] → [[Catalogo-3D]] (recursos) y [[Interfaces]] (pantallas) → tareas [[TASK-009]] · [[TASK-011]] · [[TASK-004]].
- Cada `TASK-NNN` enlaza sus documentos en `Contexto`; las dependencias están en `depende_de`.

## Propiedades que sirven para buscar
- Tareas: `id`, `estado`, `fase`, `prioridad`, `depende_de`, `tipo: tarea-codex`.
- Recursos: `id`, `categoria`, `estado_produccion`, `asset_existe`, `tarea_codex`.
- Interfaces: `id`, `estado_diseno`, `estado_implementacion`, `tarea_codex`.
- Decisiones: `id`, `estado`. Errores: `tipo: error`, `estado`, `tarea`. Entregas: `tipo: entrega-codex`, `verificacion`.

## Mantener este índice
Añade o ajusta una fila cuando aparezca un documento **de entrada** (nueva carpeta, ADR, guía, Base o Canvas de uso frecuente). **No** indexes cada ficha `RES`/`UI`/`TASK`/error/entrega: ya se encuentran por sus Bases. Actualiza `actualizado`. Para listar notas aún no mencionadas aquí, ejecuta en la raíz del vault (ignora las que ya cuelgan de un índice de área, como las de investigación, los ADR o las guías secundarias):
```powershell
Get-ChildItem docs -Recurse -Filter *.md | Where-Object { $_.FullName -notmatch '06-Tareas|Pantallas|Entregas|Errores|Pruebas|_plantillas|RES-' -and (Select-String -Path docs\00-Inicio\INDICE-IA.md -Pattern ([regex]::Escape($_.BaseName)) -Quiet) -eq $false } | Select-Object -ExpandProperty Name
```
