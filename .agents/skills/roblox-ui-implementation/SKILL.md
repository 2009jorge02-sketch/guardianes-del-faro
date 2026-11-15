---
name: roblox-ui-implementation
description: "Convierte pantallas aprobadas (fichas UI-NNN, diseños de Figma y el GDD) en interfaces nativas de Roblox para móvil y ordenador: legibles, accesibles y coherentes. Úsala cuando una tarea implemente HUD, menús, selección de cartas, resultados, ajustes o controles táctiles. No la uses para lógica de juego ni recursos 3D."
---

# roblox-ui-implementation

La interfaz **muestra estado y envía intenciones**; el servidor decide (ver `roblox-luau-engineer`). Implementa solo lo aprobado.

## Antes de empezar
1. La tarea (completa) y la ficha `docs/09-Interfaces/Pantallas/UI-NNN-*.md`: elementos, datos que muestra y de qué sistema vienen.
2. Cómo llega la especificación: `docs/09-Interfaces/Especificacion-para-Codex.md`. Estilo, paleta y reglas: `docs/03-Diseno/Arte-UI-Audio.md` (§Interfaz y §Dirección artística). Accesibilidad y dificultad: `docs/03-Diseno/Experiencia-Jugador.md`.
3. **Figma**: usa el frame solo si `figma_frame` de la ficha está relleno **y** `estado_diseno: aprobado`; es un archivo del proyecto (`docs/09-Interfaces/Figma.md`). Si no hay diseño aprobado, implementa únicamente lo que la ficha describe, sin inventar estilo, y deja la nota «sin diseño visual» en el informe. No uses ni crees archivos de Figma sin autorización.

## Reglas de implementación (Roblox nativo)
- Escala relativa (`UDim2` con Scale), `UIAspectRatioConstraint`, `UISizeConstraint` y `UITextSizeConstraint`; diseños con `UIListLayout`/`UIGridLayout` en lugar de posiciones fijas.
- **Móvil y PC**: botones táctiles ≥ 48 px, texto ≥ 16 px equivalente, márgenes seguros del dispositivo (inset/`ScreenInsets`), retrato y paisaje; soporte de teclado/ratón, táctil y mando.
- **Legibilidad y accesibilidad**: contraste suficiente, ver `Arte-UI-Audio.md`; **modo daltónico** (formas además de color), reducir efectos y asistencia de apuntado en Ajustes; no transmitir información solo por color.
- **Coherencia visual**: una sola paleta y tipografía definidas en el documento de arte; componentes reutilizables.
- Sin lógica de economía ni de daño en el cliente; todo `RemoteEvent` lo valida el servidor.
- Sin ventanas emergentes de venta ni presión de compra (`docs/03-Diseno/Monetizacion.md`).

## Verificación
1. Revisa en Studio con el emulador de dispositivos: móvil retrato/paisaje, tableta y ordenador; sin elementos fuera de pantalla ni texto cortado.
2. Comprueba táctil (≥ 48 px), teclado/ratón y mando donde aplique, y el modo daltónico y «reducir efectos» si están en el alcance.
3. Cada criterio de aceptación ✔/✘ con evidencia. Lo que requiera un móvil real queda marcado como pendiente del usuario.
4. Actualiza `estado_implementacion` de la ficha, el informe y la entrega (plantilla `entrega`). Los fallos van a `docs/07-Registro/Errores/`.

## Límites
Sin commits ni push; sin cambiar proyectos de Figma ni de Studio sin autorización.
