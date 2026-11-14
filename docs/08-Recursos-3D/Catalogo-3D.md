---
tipo: indice
categoria: recursos-3d
actualizado: 2026-11-14
cssclasses:
  - hub
---
# Catálogo de recursos 3D

Un archivo por recurso (`RES-NNN`) en la carpeta de su categoría. La información de estado vive **solo** en el YAML de cada ficha; las tablas de aquí abajo son vistas ([[Recursos-3D.base]]).

> [!warning] Estado real
> Las 21 fichas iniciales son **especificaciones de diseño** extraídas de [[Arte-UI-Audio]], [[Mecanicas]] y [[Mapas]]. **No existe ningún modelo, textura ni animación** (`asset_existe: false`, producción `pendiente`). Los datos técnicos sin fuente en el GDD se dejan vacíos o como «Sin definir».

## Categorías
| Categoría | Carpeta | Contenido inicial |
|---|---|---|
| Estructuras | `Estructuras/` | [[RES-001-Faro-principal]] · [[RES-002-Lampara-y-Foco-Mayor]] |
| Escenarios | `Escenarios/` | [[RES-003-Isla-del-Faro]] |
| Enemigos | `Enemigos/` | [[RES-007-Sombra]] · [[RES-008-Reptante]] · [[RES-009-Bruto]] · [[RES-010-Gaviota-de-sombra]] · [[RES-011-Marea-Negra]] |
| Jugador y equipo | `Jugador-y-Equipo/` | [[RES-012-Linternas]] · [[RES-013-Mascotas]] |
| Objetos interactivos | `Objetos-Interactivos/` | [[RES-006-Faroles-Reflector]] |
| Decoración | `Decoracion/` | [[RES-004-Muelle]] · [[RES-005-Rocas-bajas]] |
| Animaciones | `Animaciones/` | [[RES-019-Ciclo-de-las-Sombras]] · [[RES-020-Recoil-de-linterna]] · [[RES-021-Giro-del-foco]] |
| Efectos visuales | `VFX/` | [[RES-014-Haz-de-luz]] · [[RES-015-Destello-de-cristal]] · [[RES-016-Grieta-del-escudo]] · [[RES-017-Chispas-del-Faro]] · [[RES-018-Relampagos-lejanos]] |

Los recursos del **sistema de iluminación** son [[RES-014-Haz-de-luz]], [[RES-006-Faroles-Reflector]] y [[RES-002-Lampara-y-Foco-Mayor]].

## Vistas
**Pendientes de crear**
![[Recursos-3D.base#Pendientes de crear]]

**En produccion**
![[Recursos-3D.base#En produccion]]

**Pendientes de integracion**
![[Recursos-3D.base#Pendientes de integracion]]

**Integrados**
![[Recursos-3D.base#Integrados]]

Otras vistas: todos, por categoría, por herramienta y galería de referencias en [[Recursos-3D.base]].

## Cómo usar este catálogo
- Nuevo recurso: plantilla [[recurso-3d]] → siguiente ID libre `RES-NNN`.
- Proceso de 12 pasos: [[Flujo-de-Produccion]]. Dónde guardar archivos: [[Estructura-de-Archivos]]. Herramientas: [[Blender]] · [[Waspes-3D]].
- Presupuestos técnicos: [[Rendimiento]] y [[Politicas-y-Limites]].
