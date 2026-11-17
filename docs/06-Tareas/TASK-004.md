---
id: TASK-004
titulo: Jugador — spawn, salud y estados (activo/derribado/eliminado), entrada abstracta y cámara
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-002, TASK-003]
responsable: Codex
txx: T05
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-004 · Jugador, entrada y cámara

## Objetivo
Controlar al personaje en la isla con entrada multiplataforma abstraída y estados de salud (activo, derribado, eliminado) gestionados por el servidor ([[ADR-006-contrato-producto-v4]] D5/D15).

## Contexto
Controles: [[Mecanicas]] §Controles y §Salud, derribo, rescate y eliminación. Remotes: [[Cliente-Servidor]]. Dispositivos: [[Arte-UI-Audio]] §Interfaz.

## Requisitos
1. **Servidor** `PlayerStateService`: al unirse, el jugador aparece en un `SpawnLocation` libre; mantiene `{health, state, downUntil}` con state = activo/derribado/eliminado; API `damage(player, n)`, `rescue(target, by)` y `eliminate(player)`; emite `PlayerStateChanged`. En T05 basta la base (daño, derribo, rescate gratuito, eliminación); la reanimación con Cristales de Luz y la autorreanimación llegan en T10, cuando su coste esté fijado.
2. **Cliente** `InputController`: expone acciones abstractas `beamHeld` (bool) y `aimDirection` (Vector3 en el plano XZ) para PC (clic izq. + cursor), móvil (botón grande «Luz» mantener + arrastre del pulgar derecho) y mando (gatillo + stick derecho). Sin lógica de juego; publica señales `Signal`.
3. **Cliente** `CameraController`: cámara elevada tipo 3/4 (ángulo ~55°, distancia ~45 studs) siguiendo al jugador; sin rotación libre.
4. `UserInputService.TouchEnabled` decide la UI táctil (mínima, sin estilo final). Implementar **dos esquemas táctiles conmutables por `Config.Input.touchScheme`** ("A" por defecto): **A** = arrastrar con el pulgar derecho apunta **y enciende** la luz mientras dura el gesto (sin botón); **B** = botón grande «Luz» (mantener) + arrastre para apuntar. Motivo y método de evaluación: [[Revision-Concepto]] §4 y [[VALIDACION-PROTOTIPO]] §7.
5. Mientras el jugador no esté activo, el cliente ignora `beamHeld` y muestra un indicador simple.

## Componentes afectados (propuesta)
`src/server/Services/PlayerStateService.luau`, `src/client/Controllers/{InputController,CameraController}.luau`, `src/client/Main.client.luau`, `src/server/Main.server.luau`.

## Criterios de aceptación
- [ ] En PC, `aimDirection` sigue el cursor proyectado en el suelo y `beamHeld` refleja el clic (mostrar valores en un panel de depuración).
- [ ] En el emulador móvil de Studio aparece el botón y el arrastre produce `aimDirection`.
- [ ] Con salud 0 el jugador pasa a derribado y no usa la linterna; un compañero lo rescata en el tiempo de [[Mecanicas]] sin coste; sin rescate pasa a eliminado (prueba por comando de depuración).
- [ ] No se produce error en Local Server con 4 clientes.

## Pruebas
Play Solo; emulador de dispositivo (teléfono); Local Server 2–4 jugadores; comandos de depuración `/down` y `/eliminate` solo en Studio.

## Restricciones
El cliente no decide la salud ni el estado del jugador; nada de teclas fijas en la lógica (acciones abstractas); sin UI de estilo final.

## Entregable
Rama `codex/task-004-player` con informe.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
