---
name: roblox-asset-pipeline
description: "Gestiona el flujo de recursos 3D de Guardianes del Faro: leer la ficha RES-NNN, elegir herramienta (Blender, Waspes o Roblox Studio), optimizar para Roblox, exportar, integrar y registrar el resultado. Úsala cuando una tarea cree, revise o integre modelos, VFX o animaciones. No la uses para programar lógica ni interfaces. Nunca gasta créditos sin autorización."
---

# roblox-asset-pipeline

Una ficha `RES-NNN` es una **especificación**; un asset existe solo cuando hay un archivo real. No inventes modelos, datos técnicos ni progreso.

## Antes de empezar
1. La tarea `TASK-NNN` (completa) y la ficha del recurso en `docs/08-Recursos-3D/**/RES-NNN-*.md` (propiedades YAML y secciones).
2. Proceso de 12 pasos y estados: `docs/08-Recursos-3D/Flujo-de-Produccion.md`. Dónde guardar archivos y qué no subir a Git: `Estructura-de-Archivos.md`.
3. Presupuestos y estilo: `docs/03-Diseno/Arte-UI-Audio.md` (§Dirección artística) y `docs/04-Arquitectura/Rendimiento.md` (p. ej. ≤ 2 000 triángulos por enemigo, texturas ≤ 512², 1 material por familia, ≤ 5 instancias por enemigo). Formatos aceptados: `docs/02-Investigacion/Politicas-y-Limites.md`.

## Elegir y distinguir herramienta (campo `herramienta` de la ficha)
| Herramienta | Cuándo | Documentación |
|---|---|---|
| **Blender** | modelado/materiales propios y exportación | `docs/08-Recursos-3D/Blender.md` (instalado; Claude no lo controla; usarlo implica al usuario o a un puente aprobado) |
| **Waspes 3D** | generación o prototipado con IA | `docs/08-Recursos-3D/Waspes-3D.md` (**consume créditos**) |
| **Roblox Studio** | piezas simples, importación, ensamblado y pruebas; generación nativa del MCP de Studio | `docs/04-Arquitectura/Roblox-Studio-MCP.md` |
La herramienta la propone Claude y la aprueba el usuario; Codex no la cambia por su cuenta.

## Reglas
- **Sin créditos ni cuota sin autorización expresa** del usuario, indicando recurso y límite. Esto incluye Waspes y las herramientas `generate_*` del MCP de Studio.
- No descargues modelos de fuentes no verificadas; licencias claras (riesgo R8 en `docs/05-Planificacion/Riesgos.md`).
- Claves y tokens (Waspes, Open Cloud) nunca en el repo ni en el vault.
- Binarios: `.blend` y originales pesados fuera de Git; exportados pequeños versionables; Git LFS solo con autorización.
- Los modelos grises/greybox generados por script en el prototipo (p. ej. TASK-003) no son el asset final: no marques la ficha como `listo`.

## Procedimiento y estados
Sigue los pasos 5–12 de `Flujo-de-Produccion.md`. En la ficha, solo con evidencia: `estado_produccion` (pendiente → en_produccion → listo), `archivo_fuente`, `archivo_exportado`, `formato`, `herramienta`, `presupuesto`, `materiales_texturas`, `integracion_roblox` (pendiente → en_progreso → integrado), `asset_existe: true` y `fecha_actualizacion`.

## Verificación
1. El archivo exportado existe en la ruta anotada y respeta el presupuesto (triángulos, texturas, instancias) medido, no supuesto.
2. Integrado en Studio y funcionando según el criterio de la tarea; rendimiento comprobado con `roblox-playtest-debugger`.
3. Ficha y tarea actualizadas; resultado en el «Informe final» y en `docs/07-Registro/Entregas/` con la plantilla `entrega`.

## Límites
Sin commits ni push; sin cambiar proyectos de Studio sin autorización.
