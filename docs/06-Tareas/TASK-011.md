---
id: TASK-011
titulo: Cartas de mejora entre noches (CardService y UI)
estado: borrador
prioridad: media
fase: 2
depende_de: [TASK-008, TASK-009]
responsable: Codex
txx: T07
txx_autorizada: false
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-011 · Cartas de mejora

## Objetivo
En cada intermedio el equipo elige una de 3 cartas que modifica sus capacidades durante la partida.

## Contexto
Catálogo y efectos: [[Mecanicas]] §Cartas. Remotes `CardOffer`, `CardVote`: [[Cliente-Servidor]]. Sin azar de pago: [[Monetizacion]].

## Requisitos
1. `CardService`: genera oferta de 3 cartas distintas entre las no tomadas, por semilla de partida; recibe `CardVote {cardId}` (validado: Intermission, id en oferta, un voto por jugador); mayoría de votos emitidos gana; empate o ningún voto: la primera del orden de oferta generado con la semilla (reproducible); la votación cierra 5 s antes del fin del descanso de 25 s; en solitario elige el jugador; si nadie vota, se elige aleatoria.
2. Aplicación de efectos mediante datos en `Config.Cards` (modificadores de `BeamService`, `LighthouseService`, reflector): Lentes anchas, Prisma, Batería, Reflector, Reparación, Faro reforzado. Los modificadores se acumulan sin sobrepasar límites de `Config`.
3. Cliente `CardController`: 3 tarjetas grandes con nombre, icono provisional y descripción; temporizador; muestra resultado de la votación; icono de cartas activas en HUD.
4. Reset de cartas al terminar la partida.
5. El «Reflector» crea una torreta fija que daña con cono 40° a 6/s (sin `Humanoid`, usando matemática de cono).

## Componentes afectados (propuesta)
`src/server/Services/CardService.luau`, `src/client/Controllers/CardController.luau`, `src/shared/Config.luau` (`Cards`), modificadores en `BeamService`/`LighthouseService`.

## Criterios de aceptación
- [ ] Cada carta produce su efecto medible (prueba que compare valores antes/después).
- [ ] No se repiten cartas en la misma partida; nunca <3 distintas hasta agotar el catálogo (con 6 cartas y 4 intermedios es suficiente).
- [ ] Votos inválidos o repetidos se ignoran.
- [ ] En solitario y con 4 jugadores el flujo no se bloquea.

## Pruebas
Unitarias de generación/votación; manuales en 1 y 4 clientes.

## Restricciones
Servidor autoritativo; nada que se compre con Robux; sin animaciones pesadas.

## Entregable
Rama `codex/task-011-cards`.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
Marcar `lista` tras Puerta 1 ([[MVP]]).
