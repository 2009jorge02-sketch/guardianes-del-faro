---
id: TASK-004
titulo: Jugador — spawn, estado «Apagado», entrada abstracta y cámara
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-002, TASK-003]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-004 · Jugador, entrada y cámara

## Objetivo
Controlar al personaje en la isla con entrada multiplataforma abstraída y estado «Apagado» gestionado por el servidor.

## Contexto
Controles: [[Mecanicas]] §Controles y §Apagado. Remotes: [[Cliente-Servidor]]. Dispositivos: [[Arte-UI-Audio]] §Interfaz.

## Requisitos
1. **Servidor** `PlayerStateService`: al unirse, el jugador aparece en un `SpawnLocation` libre; mantiene estado `{stunnedUntil, immuneUntil}`; API `stun(player)` que respeta inmunidad 3 s y aturdimiento 3 s; emite `PlayerStunned`.
2. **Cliente** `InputController`: expone acciones abstractas `beamHeld` (bool) y `aimDirection` (Vector3 en el plano XZ) para PC (clic izq. + cursor), móvil (botón grande «Luz» mantener + arrastre del pulgar derecho) y mando (gatillo + stick derecho). Sin lógica de juego; publica señales `Signal`.
3. **Cliente** `CameraController`: cámara elevada tipo 3/4 (ángulo ~55°, distancia ~45 studs) siguiendo al jugador; sin rotación libre.
4. `UserInputService.TouchEnabled` decide la UI táctil (mínima, sin estilo final). Implementar **dos esquemas táctiles conmutables por `Config.Input.touchScheme`** ("A" por defecto): **A** = arrastrar con el pulgar derecho apunta **y enciende** la luz mientras dura el gesto (sin botón); **B** = botón grande «Luz» (mantener) + arrastre para apuntar. Motivo y método de evaluación: [[Revision-Concepto]] §4 y [[VALIDACION-PROTOTIPO]] §7.
5. Mientras el jugador esté «Apagado» el cliente ignora `beamHeld` y muestra un indicador simple.

## Componentes afectados (propuesta)
`src/server/Services/PlayerStateService.luau`, `src/client/Controllers/{InputController,CameraController}.luau`, `src/client/Main.client.luau`, `src/server/Main.server.luau`.

## Criterios de aceptación
- [ ] En PC, `aimDirection` sigue el cursor proyectado en el suelo y `beamHeld` refleja el clic (mostrar valores en un panel de depuración).
- [ ] En el emulador móvil de Studio aparece el botón y el arrastre produce `aimDirection`.
- [ ] `stun()` desactiva `beamHeld` 3 s y aplica 3 s de inmunidad (prueba por comando de depuración).
- [ ] No se produce error en Local Server con 4 clientes.

## Pruebas
Play Solo; emulador de dispositivo (teléfono); Local Server 2–4 jugadores; comando de depuración `/stun` solo en Studio.

## Restricciones
El cliente no decide el estado «Apagado»; nada de teclas fijas en la lógica (acciones abstractas); sin UI de estilo final.

## Entregable
Rama `codex/task-004-player` con informe.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
