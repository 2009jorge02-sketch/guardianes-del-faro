---
tipo: proceso
categoria: coordinacion
actualizado: 2026-11-15
---
# Flujo de trabajo Claude ↔ Codex

Canvas del flujo: [[Mapa-Flujo-Claude-Codex.canvas]] (Canvas). Panel: [[Centro-de-Control]]. Reglas de cada agente: [[CLAUDE]] y [[AGENTS]] (canónicas; esta nota solo coordina).

## Reparto
- **Claude:** investigación, diseño, arquitectura, planificación y revisión.
- **Codex:** implementación, pruebas y optimización.
- **El usuario:** lanza cada herramienta y aprueba lo sensible (commits y push, instalaciones, costes, permisos, cambios de modelo o esfuerzo).

## Canales (no hay conexión directa)
- **Archivos del vault/repositorio** (`docs/`), leídos por ambos (lectura progresiva: [[INDICE-IA]]).
- **Git**, una rama por tarea (`codex/task-NNN-slug`, ver [[AGENTS]]). Sin commits ni push automáticos sin permiso del usuario.

## Ciclo
1. Claude prepara la tarea (`TASK-NNN`, estado `lista`) y, si hace falta, fichas de recurso o interfaz.
2. Codex toma la primera tarea **ejecutable** (`lista` y dependencias `hecha`, vista [[Tareas-Ejecutables.base]]), crea su rama, cambia `estado: en_progreso`, rellena `rama` y `fecha_actualizacion`.
3. Codex trabaja y deja **puntos de control** en la tarea (progreso por requisito, archivos modificados, pruebas pendientes).
4. Codex termina: «Informe final», nota de entrega (plantilla `entrega`), `estado: en_revision`, entrada en [[PROGRESS]].
5. Claude revisa con evidencias: `hecha`, o crea `TASK-NNN-fix` / registra un error ([[Pruebas-y-Errores]]).
6. Se actualiza la ficha del recurso o interfaz afectada.

## Asignación y conflictos
- **Una tarea activa por responsable** (`en_progreso`). Antes de tomar otra, cerrar o pasar a `en_revision`/`bloqueada` la actual.
- **Una tarea = una rama = un responsable.** Dos agentes nunca tocan la misma ruta a la vez; si comparten carpeta de trabajo, edita uno solo cada vez (o worktrees separados).
- **Propiedad por ruta:** Codex escribe en `src/`, `tests/` y configuración de herramientas; en `docs/` solo en su tarea, [[PROGRESS]], entregas, errores y pruebas. Claude escribe el resto de `docs/` y las fichas `RES`/`UI`.
- Una tarea `en_progreso` no la edita Claude salvo para responder en «Bloqueos / preguntas». Codex no cambia diseño ni ADR: lo propone en «Bloqueos».
- Antes de empezar: `git status` y `git fetch`; si la base cambió, actualizar la rama antes de seguir. Ante un conflicto de Git: parar, no sobrescribir y avisar al usuario.
- `AGENTS.md`, `CLAUDE.md` e `INDICE-IA` los mantiene Claude; Codex propone cambios.

## Reanudar sin repetir trabajo
La plantilla [[tarea]] incluye «Progreso por requisito», «Último punto de control», «Archivos modificados», «Pruebas pendientes» e «Instrucciones para reanudar». Procedimiento: leer la tarea completa → `git status`/`git log` de la rama → pruebas y linters → continuar por el primer requisito sin marcar → registrar un nuevo punto de control. El estado vive en archivos, no en la conversación.

## Recuperación ante fallos
- Fallo de herramienta o prueba: registrar `ERR-NNN` (plantilla `error`) con comando y salida; no avanzar sobre un fallo no entendido.
- Tarea rechazada: Claude crea `TASK-NNN-fix`.
- MCP o app caída: Obsidian MCP requiere Obsidian abierto y reiniciar el cliente si la sesión empezó con él cerrado; Studio MCP requiere una instancia de Studio abierta. Estado real en [[Estado-de-Conexiones]].
- Sesión interrumpida: reanudar con el apartado anterior.

## Propiedades de tarea (YAML)
`id` · `titulo` · `estado` (`borrador` · `lista` · `en_progreso` · `en_revision` · `hecha` · `bloqueada`) · `prioridad` · `fase` · `responsable` · `depende_de` · `creado` · `tipo: tarea-codex` · `fecha_actualizacion` · `rama` (opcional, nueva en la plantilla).
`depende_de` es el nombre histórico de las «dependencias» (se mantiene para no romper [[AGENTS]]; la Base lo muestra como «Dependencias»). Al cambiar de estado, actualizar también `fecha_actualizacion`.

## Reglas
- Un dato, un lugar: no repetir estados en tablas manuales (la tabla de [[TASKS]] es un resumen histórico; la verdad es el YAML).
- Nada pasa a `hecha` sin evidencias y sin entrega `verificada` ([[Actividad-Real]]).
- Ningún agente cambia de modelo o esfuerzo por su cuenta: se detiene, deja el estado en la tarea y pide autorización al usuario.
