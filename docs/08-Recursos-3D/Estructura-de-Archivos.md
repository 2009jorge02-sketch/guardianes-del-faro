---
tipo: proceso
categoria: recursos-3d
estado: propuesta (no implementada; no se ha creado ninguna carpeta de assets)
actualizado: 2026-11-14
---
# Estructura de archivos de recursos 3D

Propuesta compatible con el repositorio y con Rojo ([[ADR-002-herramientas]]). **Aún no se ha creado nada fuera de `docs/`**; la aplicará Codex cuando exista el primer recurso real.

## Propuesta
```
assets/3d/
  fuentes/        # .blend y proyectos de origen (NO versionados en Git por defecto)
  exportados/     # .fbx / .glb optimizados listos para Roblox (pequeños, versionables)
  referencias/    # imágenes de referencia ligeras (o dentro del vault, en docs/08-Recursos-3D/)
```
Convención de nombres: `RES-007-Sombra.blend` → `RES-007-Sombra.fbx`; el ID enlaza archivo, ficha y tarea.

## Estrategia para binarios (evitar inflar Git)
1. `.blend` y otros originales pesados: **fuera de Git** (carpeta local o almacenamiento externo que el usuario elija); anotar su ruta en `archivo_fuente`. Añadir `assets/3d/fuentes/` a `.gitignore` cuando se cree.
2. Exportados pequeños (orientativo: < 5 MB cada uno): se pueden versionar en `assets/3d/exportados/`.
3. Si el volumen crece, valorar **Git LFS**. Requiere instalar/configurar algo y se **pide autorización** antes.
4. Lo que se sube a Roblox queda referenciado por su Asset ID en `Config` o en la ficha, nunca por claves en el repo.
5. Nunca guardar claves API ni credenciales (Roblox Open Cloud, Waspes) en el vault ni en el repositorio.

## Rojo
Los modelos importados a Studio pueden mapearse con Rojo (`.rbxm`/`.rbxmx`) cuando Codex lo defina en `default.project.json` ([[TASK-001]]). La decisión concreta se registra como ADR cuando llegue el primer recurso.
