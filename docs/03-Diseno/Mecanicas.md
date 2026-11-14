---
tipo: diseno
estado: valores iniciales de balance (a ajustar en prototipo)
---
# Mecánicas y balance (fuente única de cifras)

Contexto: [[GDD]]. Todos los valores irán a un módulo `Config` ([[ARCHITECTURE]]). Unidad de distancia: studs.

## Controles
| Acción | PC | Móvil |
|---|---|---|
| Moverse | WASD | Joystick izquierdo |
| Encender linterna | Mantener clic izq. | Botón grande derecho (mantener) |
| Apuntar | Cursor (el haz sigue al ratón en el plano del suelo) | Arrastrar pulgar derecho (esquema A: también enciende); **asistencia de apuntado** hacia la Sombra más cercana en el cono |
| Subir/bajar del Foco Mayor | E (interactuar) | Botón contextual |
| Elegir carta | Clic / 1-2-3 | Toque |
Salto permitido. Sin sprint en MVP.

## Linterna (cada jugador)
- Cono 35°, alcance 28, daño 12/s mientras ilumina. Daño por *tick* de 0,1 s calculado en servidor.
- **Carga** 100: se gasta 15/s encendida; se recarga 25/s tras 0,5 s apagada. Si llega a 0 → **sobrecalentada** 1,5 s sin poder usarla.
- Entrada del cliente = «encendida/apagada + dirección» (≤20 Hz); el servidor valida límites y calcula impactos.

### Parámetros de validación (añadidos tras [[Revision-Concepto]])
- `overlapBonus`: multiplicador de daño cuando un enemigo está en ≥2 conos. **1.0 (desactivado)** por defecto; probar **1.5** en playtest.
- `touchScheme`: "A" (arrastrar = apuntar y encender) por defecto o "B" (botón + arrastre).
- `pulses`: cada noche se divide en 2–3 pulsos con respiro de 3–5 s.

## Foco Mayor (en la galería del faro)
- Una sola plaza. Jugador subido: cono 50°, alcance 60, daño 30/s, sin gasto de Carga, gira a 120°/s hacia el apuntado.
- **Sin jugador:** modo automático: barrido 20°/s, 8 de daño/s (el juego nunca depende de un operador).
- Subir/bajar tarda 1 s (escalera rápida); si el operador se «apaga», baja solo.

## Integridad del Faro
Integridad 100 (+mejoras). Enemigos en contacto con el faro le infligen daño. No se repara pasivamente; hay carta de reparación.

## «Apagado» (jugadores)
Si una Sombra toca a un jugador: 3 s sin linterna ni acciones, empuje leve, 3 s de inmunidad después. Sin muerte, sin pérdida de progreso.

## Enemigos (MVP: 1–3 tipos; **sin `Humanoid`**, tope 60 simultáneos)
| Tipo | PV | Velocidad | Daño al faro | Comportamiento | Fase |
|---|---|---|---|---|---|
| Sombra | 20 | 8 | 5/s al contacto | camina recto al faro | Prototipo |
| Reptante | 10 | 14 | 3/s | rápido, llega en grupos | MVP |
| Bruto | 120 | 4 | 12/s | solo recibe daño pleno con luz de ≥1,5 s seguida (escudo de cristal se agrieta) | MVP |
| Gaviota de sombra (aérea) | 15 | 10 | ataca la lámpara | vuela, obliga al Foco Mayor | Alfa |
| Marea Negra (jefe) | 1500 | 3 | 25/s | invoca Reptantes; luz de varios jugadores | Alfa |
Las Sombras reciben daño **solo** si están dentro de un cono de luz; fuera de la luz son más rápidas (+25 %) → presión por barrer.

## Noches (oleadas)
| Noche | Duración | Spawn (aprox.) | Tipos |
|---|---|---|---|
| 1 | 75 s | 25 | Sombra |
| 2 | 85 s | 35 | Sombra, Reptante |
| 3 | 95 s | 45 | + Bruto |
| 4 | 105 s | 55 | todos |
| 5 | 120 s | 70 | todos + oleada final |
Escalado por nº de jugadores: ×(0,7 + 0,3·n). Intermedio entre noches 30 s. Spawn en anillo a radio 60 desde el faro, tope 60 vivos.

## Cartas de mejora (elige 1 de 3 al azar entre las no tomadas; efecto para todo el equipo)
| Carta | Efecto |
|---|---|
| Lentes anchas | cono linterna +10° |
| Prisma | daño de luz +20 % |
| Batería | Carga máx. +30 y recarga +20 % |
| Reflector | torreta de luz fija en el borde de la isla (daño 6/s, cono 40°) |
| Reparación | restaura 25 de Integridad |
| Faro reforzado | Integridad máx. +30 |
Elección **sin coste**; el azar solo decide qué cartas se ofrecen (no hay pago involucrado).

## Dificultades «Tormenta» (opcionales, Alfa)
Modificadores voluntarios (más Sombras, menos Carga…) con más recompensa cosmética; nunca obligatorios.

## Equilibrio objetivo (a medir)
Solo: ~70 % de victoria en N1-3 tras ≥3 partidas, ~35 % partida completa. Cuatro: ~55 %. Medir en playtests.

## Relacionado (añadido en la mejora del vault)
- Índice de enemigos: [[Enemigos]] · Flujo de partida: [[Flujo-de-Jugabilidad.canvas]] · Mapa de diseño: [[Centro-de-Diseno.canvas]]
- Interfaces que muestran estas reglas: [[UI-002-HUD]] · [[UI-003-Seleccion-de-carta]] · [[UI-007-Controles-moviles]]
