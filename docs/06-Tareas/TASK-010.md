---
id: TASK-010
titulo: Foco Mayor — SpotlightService y control cliente
estado: borrador
prioridad: media
fase: 2
depende_de: [TASK-006, TASK-008, TASK-009]
responsable: Codex
txx: T10
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-010 · Foco Mayor

## Objetivo
Añadir el haz grande del faro: modo automático y modo manual con un operador voluntario.

## Contexto
[[Mecanicas]] §Foco Mayor; remotes `SpotlightToggle` y `SpotlightAim`: [[Cliente-Servidor]]; pilar 3 ([[Pilares]]): el juego no depende de un operador.

## Requisitos
1. `SpotlightService`: una plaza; `SpotlightToggle {enter}` valida distancia a la escalera, plaza libre, jugador activo y cooldown 1 s; sube/baja en 1 s.
2. Modo auto sin operador: barrido 20°/s, 8 daño/s, cono 50°, alcance 60 desde `LampPivot`.
3. Modo manual: 30 daño/s, giro máx. 120°/s hacia `SpotlightAim`, sin gasto de Carga; si el operador es derribado o sale, vuelve a auto.
4. Cliente: prompt contextual, visual del haz grande (reutilizar estilo de [[TASK-006]]), cámara estable.
5. Daño y marca `lit` mediante la misma matemática de cono (`Cone.luau`).

## Componentes afectados (propuesta)
`src/server/Services/SpotlightService.luau`, `src/client/Controllers/SpotlightController.luau`, `Config` (solo lectura).

## Criterios de aceptación
- [ ] Sin operador, el foco barre y daña a 8/s (medido).
- [ ] Un jugador sube, apunta y daña a 30/s; al bajar o ser derribado vuelve a auto.
- [ ] Dos jugadores no pueden ocupar la plaza a la vez.
- [ ] Remotes validados (distancia, estado, tasa).

## Pruebas
Manual 1, 2 y 4 clientes; script de remote malformado.

## Restricciones
Solo servidor decide ocupación y daño.

## Entregable
Rama `codex/task-010-spotlight`.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
Marcar `lista` tras la puerta de ADR-004 ([[MVP]]). Txx dueña: T10 ([[ADR-006-contrato-producto-v4]] §Relación).
