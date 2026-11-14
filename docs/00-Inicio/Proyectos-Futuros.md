---
tipo: propuesta
categoria: navegacion
estado: propuesta (no implementada; no se ha movido ni modificado ningún otro proyecto)
actualizado: 2026-11-14
---
# Propuesta: vault multiproyecto

**Nada de esto está implantado.** No se han movido repositorios ni tocado Rose AI. Esta nota solo describe cómo podría crecer el sistema sin mezclar proyectos.

## Situación actual
- Este vault es la carpeta del repositorio `Juego roblox 1` (proyecto único: Guardianes del Faro).
- En la carpeta superior `juego roblox1/` existe además un `.obsidian` antiguo (original conservado); no es el vault activo.

## Opción recomendada: un vault por proyecto + plantillas reutilizables
- Cada proyecto mantiene **su propio repositorio y vault** (aislamiento total, ningún riesgo para producción).
- Lo reutilizable se copia desde un «kit base»: plantillas (`_plantillas/`), snippet CSS, las Bases (Tareas, Recursos, Interfaces), convenciones de [[Flujo-Claude-Codex]] y el esquema de fichas [[recurso-3d]] / [[interfaz]].
- Para estrenar un proyecto: copiar el kit, renombrar carpetas y ajustar el YAML (`tipo`, `proyecto`).

## Opción B: vault «Panel de proyectos» superior
- Un vault en una carpeta padre con una nota `Proyectos` que enlace a cada proyecto (Guardianes del Faro, Rose AI, otros juegos Roblox, ideas).
- Riesgos: rutas largas, el gráfico mezcla proyectos y las Bases con `file.inFolder` deberían acotarse por carpeta.
- Requeriría decidir qué carpeta es la raíz y si cada repositorio Git queda como subcarpeta independiente.

## Cómo se implantaría (más adelante, con autorización)
1. Elegir la opción.
2. Copiar el kit a un proyecto de prueba, nunca a Rose AI directamente.
3. Verificar enlaces y Bases.
4. Solo entonces extender a otros proyectos.

## Convenciones propuestas
- Propiedad `proyecto: guardianes-del-faro` en notas nuevas (no añadida aún a las existentes para no tocar el trabajo hecho).
- Prefijos de ID por proyecto (`TASK-`, `RES-`, `UI-`) con carpeta propia, para no mezclar producciones.
