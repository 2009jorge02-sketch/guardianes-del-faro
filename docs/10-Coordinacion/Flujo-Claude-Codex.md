---
tipo: proceso
categoria: coordinacion
actualizado: 2026-11-14
---
# Flujo de trabajo Claude ↔ Codex

Canvas del flujo: [[Mapa-Flujo-Claude-Codex.canvas]] (Canvas). Panel: [[Centro-de-Control]].

## Canales (no hay conexión directa)
- **Archivos del vault/repositorio** (`docs/`), leídos por ambos.
- **Git** en la rama de cada tarea (`codex/task-NNN-slug`, ver [[AGENTS]]). Sin commits ni push automáticos sin permiso del usuario.
- El **usuario** lanza cada herramienta y aprueba lo sensible.

## Ciclo
1. Claude prepara la tarea (`TASK-NNN`, estado `lista`) y, si hace falta, fichas de recurso o interfaz.
2. Codex toma la primera `lista` con dependencias `hecha`, cambia `estado: en_progreso` y actualiza `fecha_actualizacion`.
3. Codex termina: rellena «Informe final», `estado: en_revision`, entrada en [[PROGRESS]].
4. Claude revisa con evidencias ([[CLAUDE]]): `hecha`, o crea `TASK-NNN-fix` / registra un error ([[Pruebas-y-Errores]]).
5. Se actualiza la ficha del recurso o interfaz afectada.

## Propiedades de tarea (YAML)
`id` · `titulo` · `estado` (`borrador` · `lista` · `en_progreso` · `en_revision` · `hecha` · `bloqueada`) · `prioridad` · `fase` · `responsable` · `depende_de` · `creado` · `fecha_actualizacion` · `tipo: tarea-codex`.
`depende_de` es el nombre histórico de las «dependencias» (se mantiene para no romper [[AGENTS]]; la Base lo muestra como «Dependencias»).
Al cambiar de estado, actualizar también `fecha_actualizacion`.

## Reglas
- Un dato, un lugar: no repetir estados en tablas manuales (la tabla de [[TASKS]] es un resumen histórico; la verdad es el YAML).
- Nada pasa a `hecha` sin evidencias.
