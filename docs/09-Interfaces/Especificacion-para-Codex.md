---
tipo: proceso
categoria: interfaces
actualizado: 2026-11-14
---
# Cómo recibe Codex las especificaciones de interfaz

Codex no habla con Claude ni con Figma automáticamente: lee **archivos del repositorio** ([[Flujo-Claude-Codex]]).

## Paquete mínimo por pantalla
1. **Ficha `UI-NNN`** ([[Interfaces]]): elementos, comportamiento, datos que muestra y de qué sistema vienen.
2. **Tarea `TASK-NNN`** en `docs/06-Tareas/` con requisitos y criterios de aceptación; enlaza la ficha.
3. **Diseño visual:** URL del frame en `figma_frame` (si existe). Si Codex no puede abrir Figma, el usuario adjunta una exportación (PNG) o describe medidas; mientras tanto vale la descripción textual de la ficha.
4. **Reglas de plataforma:** táctil ≥ 48 px, texto ≥ 16 px equivalente, teclado/ratón/mando ([[Arte-UI-Audio]]).
5. **Reglas técnicas:** el servidor es la autoridad; la UI solo muestra estado y envía intenciones validadas ([[Cliente-Servidor]], [[Seguridad]]).

## Devolución
Codex rellena el «Informe final» de la tarea, actualiza `estado_implementacion` de la ficha y añade el resultado a [[PROGRESS]]. Claude revisa y marca `estado_diseno`/tarea ([[Centro-de-Control]]).
