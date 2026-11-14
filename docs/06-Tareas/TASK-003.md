---
id: TASK-003
titulo: MapBuilder — isla y faro greybox con iluminación nocturna
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-002]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-003 · Isla y faro (greybox por código)

## Objetivo
Generar por script la isla y el faro del prototipo para no depender de edición manual en Studio.

## Contexto
Especificación en [[Mapas]]; paleta en [[Arte-UI-Audio]]. Arquitectura en [[ARCHITECTURE]].

## Requisitos
1. `src/server/Services/MapBuilder.luau` con `MapBuilder.build(): Model` que crea en `Workspace.Map`:
   - Isla: cilindro radio 45, altura 4, color gris-arena; mar: plano grande azul oscuro (sin colisión relevante).
   - Faro: base (cilindro radio 6, altura 30), galería (disco radio 8 a altura 30) con lámpara (esfera neón ámbar); `Part` invisible `LampPivot` en el centro de la galería (para el Foco Mayor).
   - Escalera/rampa de acceso al faro y punto de interacción `SpotlightPrompt` (ProximityPrompt desactivado por ahora).
   - 4 rocas bajas decorativas y muelle simple.
   - `SpawnRing`: 10 `Attachment`/`Part` invisibles a radio 60 del centro (atributos `Index`).
   - `PlayerSpawns`: 4 `SpawnLocation` a radio 12 alrededor del faro.
2. Iluminación nocturna: `Lighting` (ClockTime 20, Ambient azul oscuro), `Atmosphere`, sin sombras globales; función `MapBuilder.setNight(n)` ajusta la intensidad (1 = atardecer, 5 = tormenta).
3. Todas las partes `Anchored`, `CanQuery=false` donde no se necesite, mallas simples (primitivas).
4. Constantes desde `Config`.

## Componentes afectados (propuesta)
`src/server/Services/MapBuilder.luau`, `src/server/Main.server.luau` (llamar a build al arrancar).

## Criterios de aceptación
- [ ] Al dar Play aparece la isla con el faro centrado y los 4 jugadores spawnean en torno a él.
- [ ] `Workspace.Map` contiene `SpawnRing` con 10 puntos a radio 60 ±0.1 (comprobado por script de prueba en el informe).
- [ ] `setNight(1..5)` cambia visiblemente la iluminación.
- [ ] Recuento de instancias de `Map` ≤ 150 (anotar cifra).
- [ ] Sin errores/avisos en Output.

## Pruebas
Play Solo y Local Server (2 jugadores): comprobar spawns, que no se cae del mundo y que la lámpara es visible desde la isla.

## Restricciones
Sin texturas externas; sin `MeshPart` importadas; sin `Humanoid` extra.

## Entregable
Rama `codex/task-003-map` + capturas descritas en el informe.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
