---
tipo: integracion
herramienta: Blender
estado_conexion: instalado en el PC (Blender 5.3); sin conexión con Claude
verificado: 2026-11-14
---
# Blender

## Estado verificado
- Instalado en `C:\Program Files\Blender Foundation\Blender 5.3` (comprobado por la existencia de la carpeta).
- **Claude no tiene ninguna conexión ni herramienta para controlar Blender** en esta sesión. No se ha abierto, ejecutado ni modificado nada.
- Codex: no verificado (no hay evidencia de que tenga un puente con Blender).

## Uso previsto
Modelado, materiales y exportación de los recursos de [[Catalogo-3D]] siguiendo [[Flujo-de-Produccion]]. Ficha: `herramienta: blender`.

## Directrices de producción (derivadas de [[Arte-UI-Audio]] y [[Rendimiento]])
- Low-poly estilizado; ≤ 2 000 triángulos por enemigo; texturas ≤ 512²; un material compartido por familia.
- Escala en studs coherente con el mapa ([[Mapas]]); decidir y documentar la equivalencia unidad Blender ↔ studs al crear el primer recurso.
- Exportar a un formato aceptado por la importación de Roblox ([[Politicas-y-Limites]]).
- Archivos según [[Estructura-de-Archivos]].

## Pendiente
- Si se quiere que una IA maneje Blender, hace falta un puente (por ejemplo un servidor MCP) que **requiere instalación y autorización del usuario**; no se ha instalado.
