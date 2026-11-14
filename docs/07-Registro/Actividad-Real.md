---
tipo: indice
categoria: registro
actualizado: 2026-11-14
cssclasses:
  - hub
---
# Actividad real del proyecto

Un **avance real** es una entrega de Codex **verificada por Claude** (commit o rama, pruebas ejecutadas y criterios de aceptación comprobados), no un archivo que cambió hace poco. Por eso esta página no usa la fecha de modificación.

**Todavía no hay entregas registradas**: Codex no ha empezado ([[TASK-001]] sigue sin ejecutarse).

## Cómo se registra
1. Al terminar una tarea, Codex crea una nota en `docs/07-Registro/Entregas/` con la plantilla [[entrega]] (`verificacion: sin_verificar`) y cambia la tarea a `en_revision`.
2. Claude revisa con la plantilla [[revision]] y, si todo se cumple, pone `verificacion: verificada` y la tarea pasa a `hecha`; si no, `rechazada` y se crea `TASK-NNN-fix`.
3. Las vistas de abajo se rellenan solas.

## Entregas verificadas (avance real)
![[Actividad.base#Entregas verificadas]]

## Entregas pendientes de verificar
![[Actividad.base#Entregas pendientes de verificar]]

## Revisiones
![[Actividad.base#Revisiones]]

## Archivos modificados recientemente (solo referencia, no es avance)
![[Registro.base#Modificados recientemente]]

Historia de la planificación: [[PROGRESS]] · [[Auditoria-2026-11-14]].
