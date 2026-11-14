---
tipo: panel
actualizado: 2026-11-14
cssclasses:
  - dashboard
---
# Centro de control Claude ↔ Codex

> [!estado] Fuente de verdad única
> El estado de una tarea vive **solo** en el YAML (`estado`) de `docs/06-Tareas/TASK-NNN.md`. Todo lo de esta página son **vistas**; no hay copias. «Ejecutable» = `estado: lista` **y** todas sus dependencias en `hecha` (se calcula en [[Tareas-Ejecutables.base]]). No hay comunicación automática entre Claude y Codex: se coordinan con archivos y Git ([[Flujo-Claude-Codex]]).

## Ejecutables ahora (listas para Codex)
![[Tareas-Ejecutables.base#Ejecutables ahora]]

## Documentadas, pero esperando dependencias
![[Tareas-Ejecutables.base#Documentadas con dependencias pendientes]]

## En ejecución
![[Tareas.base#En progreso]]

## Resultados pendientes de revisión (Claude)
![[Tareas.base#En revision]]

## Bloqueadas
![[Tareas.base#Bloqueadas]]

## Avance real (entregas y revisiones verificadas)
![[Actividad.base#Entregas verificadas]]

Entregas sin verificar y revisiones: [[Actividad-Real]].

## Errores detectados
![[Errores.base#Abiertos]]

## Decisiones pendientes
![[Decisiones.base#Pendientes]]

Decisiones del usuario aún abiertas: [[Riesgos]]. Orden recomendado y puertas de calidad: [[TASKS]] · [[ROADMAP]] · [[MVP]]. Bitácora: [[PROGRESS]].

## Quién hace qué
| Claude Code | Codex |
|---|---|
| Investigar, diseñar, planificar | Programar, implementar mecánicas y sistemas |
| Organizar tareas y criterios | Integrar recursos y ejecutar pruebas |
| Revisar resultados, detectar problemas | Corregir errores y optimizar |
| Preparar instrucciones, mantener documentación | Registrar entregas y resultados |

Instrucciones: [[CLAUDE]] · [[AGENTS]] · [[ENTREGA-PARA-CODEX]].
