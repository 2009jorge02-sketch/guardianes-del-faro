---
tipo: indice
categoria: navegacion
actualizado: 2026-11-14
cssclasses:
  - hub
---
# Mapa de conocimiento

Todas las conexiones son enlaces reales entre notas. Vista gráfica: ribbon/paleta de comandos → **Abrir vista de gráfico**.

## Las 13 categorías y dónde viven
| # | Categoría | Notas principales |
|---|---|---|
| 1 | Visión | [[Concepto]] · [[Pilares]] · [[Publico-objetivo]] |
| 2 | Investigación | [[Investigacion-Indice]] |
| 3 | Mecánicas | [[Mecanicas]] · [[Progresion-Economia]] · [[Monetizacion]] |
| 4 | Diseño | [[GDD]] · [[Arte-UI-Audio]] · [[Experiencia-Jugador]] · [[Centro-de-Diseno.canvas]] |
| 5 | Mapas | [[Mapas]] · [[RES-003-Isla-del-Faro]] |
| 6 | Enemigos | [[Enemigos]] |
| 7 | Arquitectura | [[ARCHITECTURE]] · [[Cliente-Servidor]] · [[Seguridad]] · [[Rendimiento]] · [[Arquitectura-de-Sistemas.canvas]] |
| 8 | Recursos 3D | [[Catalogo-3D]] |
| 9 | Interfaces | [[Interfaces]] · [[Figma]] |
| 10 | Programación | [[Setup-Entorno]] · [[AGENTS]] · [[ADR-002-herramientas]] |
| 11 | Tareas | [[Tareas.base]] · [[Tareas-Ejecutables.base]] · [[TASKS]] · [[Centro-de-Control]] · [[Actividad-Real]] |
| 12 | Pruebas | [[Pruebas-y-Errores]] · [[VALIDACION-PROTOTIPO]] |
| 13 | Decisiones | [[Decisiones.base]] · [[Riesgos]] |

## Colores de la vista gráfica
`.obsidian/graph.json` define grupos por carpeta (se aplican solos al abrir el gráfico):

| Carpeta | Color |
|---|---|
| `00-Inicio` | gris azulado |
| `01-Vision` | ámbar |
| `02-Investigacion` | gris pizarra |
| `03-Diseno` | morado |
| `04-Arquitectura` | azul cielo |
| `05-Planificacion` | verde |
| `06-Tareas` | verde esmeralda |
| `07-Registro` | rojo |
| `08-Recursos-3D` | naranja |
| `09-Interfaces` | rosa |
| `10-Coordinacion` | turquesa |

Se excluyen del gráfico las plantillas (`search: -path:docs/_plantillas`); las carpetas de respaldo (`.obsidian-backup-*`) no las indexa Obsidian.

## Si no ves los colores o filtros (manual)
1. Abre el gráfico → engranaje (⚙) → sección **Grupos**.
2. Si faltan, pulsa **Nuevo grupo** y escribe la consulta `path:docs/03-Diseno` (cambia la carpeta) y elige el color.
3. Filtros útiles: en **Filtros** desactiva «Huérfanos» para ver solo lo conectado, o escribe en el buscador `path:docs/08-Recursos-3D`.
4. Si un cambio hecho a mano no persiste, restaura `.obsidian-backup-2026-11-14/` (ver [[Movil]] para otros ajustes) o borra `graph.json` para volver a los valores por defecto.
5. **La vista gráfica no se ha abierto visualmente en esta sesión**; solo se validó el formato del archivo.

> [!note] La vista gráfica es secundaria
> Para trabajar usa [[Home]], [[Centro-de-Control]] y las Bases; el gráfico sirve para ver relaciones, no para navegar el día a día.
