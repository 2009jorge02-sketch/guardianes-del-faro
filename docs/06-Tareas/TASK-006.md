---
id: TASK-006
titulo: Linterna — BeamService (servidor) y BeamController (visual)
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-004, TASK-005]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-006 · Linterna y haz de luz

## Objetivo
Implementar la mecánica central: apuntar y mantener la luz daña a las Sombras dentro del cono, con Carga y sobrecalentamiento, validada en servidor.

## Contexto
Reglas y cifras: [[Mecanicas]] §Linterna. Remotes `BeamInput` y `BeamState`: [[Cliente-Servidor]]. Validación: [[Seguridad]]. Pilar 1: [[Pilares]].

## Requisitos
1. **Cliente** `BeamController`: envía `BeamInput {on, dir}` a ≤20 Hz **solo cuando cambian o cada 50 ms mientras está encendida**; dibuja el haz del jugador local y de los demás (a partir de `BeamState`) con un cono translúcido neón ámbar + luz puntual; feedback inmediato (<100 ms) al pulsar.
2. **Servidor** `BeamService`: mantiene `{on, dir, charge, overheatUntil}` por jugador; valida entrada ([[Seguridad]]: tipos, `dir` finita y unitaria, rate-limit 25 msg/s, no «Apagado», estado `Night`); a 10 Hz calcula impacto: enemigo dentro de cono 35° y alcance 28 desde la posición del jugador ⇒ `EnemyService.damage(id, 12*0.1)`.
3. Carga 100: gasto 15/s, recarga 25/s tras 0,5 s apagada, sobrecalentado 1,5 s al llegar a 0 (valores de `Config`). Replicar `charge` al cliente propietario por atributo del jugador.
4. Marcar enemigos iluminados (`lit = true` ese tick) para la regla de velocidad de [[TASK-005]].
5. Difundir `BeamState` (UnreliableRemoteEvent) a los demás clientes a ≤10 Hz.
6. Asistencia de apuntado móvil: en cliente, si hay una Sombra a ≤10° del cono, ajustar `dir` suavemente (parámetro en `Config`, desactivable en Ajustes futuros).
7. **Cruce de haces (parámetro de validación):** `Config.Beam.overlapBonus` (por defecto **1.0 = desactivado**). Si un enemigo está dentro de ≥2 conos (linterna+linterna o +Foco), el daño de ese tick se multiplica por `overlapBonus` (a probar con **1.5** en playtest, ver [[Revision-Concepto]] §1). Documentar cómo activarlo.
8. Matemática del cono en módulo puro `shared/Util/Cone.luau` con pruebas unitarias.

## Componentes afectados (propuesta)
`src/server/Services/BeamService.luau`, `src/client/Controllers/BeamController.luau`, `src/shared/Util/Cone.luau`, `tests/cone_test.luau`.

## Criterios de aceptación
- [ ] Un enemigo dentro del cono recibe daño por tick; uno fuera no (prueba unitaria + manual).
- [ ] La Carga baja y se recarga con los valores de `Config`; el sobrecalentamiento bloquea 1,5 s.
- [ ] Un cliente que envía `dir` NaN o >25 msg/s es ignorado (prueba con script de ataque en Studio descrita en el informe).
- [ ] El haz de otro jugador se ve en Local Server (2 clientes).
- [ ] El primer feedback visual aparece en el mismo frame de entrada del cliente local.
- [ ] Con 60 enemigos, `BeamService` cuesta <1 ms por tick (medido).

## Pruebas
Unitarias del cono; manuales (PC + emulador móvil); ataque simulado de remote malformado.

## Restricciones
Daño solo en servidor; ningún `Raycast` por enemigo; sin `Touched`; cliente no envía daño.

## Entregable
Rama `codex/task-006-beam` con informe y mediciones.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
