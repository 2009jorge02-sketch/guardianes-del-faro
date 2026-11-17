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
- Subir/bajar tarda 1 s (escalera rápida); si el operador es derribado, baja solo.

## Integridad del Faro
Integridad 100 (+mejoras). Enemigos en contacto con el faro le infligen daño. No se repara pasivamente; hay carta de reparación.

## Salud, derribo, rescate y eliminación (ADR-006 D5; sustituye al «Apagado»)
Valores **propuestos** (Registro V4.1 §5.2), pendientes de balance antes de implementar:
- **Salud** por jugador. Las Sombras dañan sobre todo a quien sale del faro (expediciones); el valor exacto lo fija T10.
- **Derribado** a 0 de salud: 10–12 s en el suelo. Un compañero lo **rescata** en el sitio en 5–7 s, expuesto a ataques; no gasta recurso. Hay un límite contra rescates consecutivos abusivos.
- **Eliminado** si nadie llega: queda fuera esa noche y su «eco de luz» aparece en la **estación de reanimación**, cerca del faro.
- **Estación:** reanimar consume **Cristales de Luz compartidos** del equipo (D15), los mismos que sirven para reparar el faro o activar una defensa extraordinaria; usarlo en reanimar es renunciar a eso. La activación tarda varios segundos y aleja a un jugador de la defensa. Se avisa al equipo del gasto; en grupo se evalúa una confirmación por mayoría para evitar griefing.
- **Solitario:** autorreanimación limitada con coste en Cristales de Luz si quedan; si no, derrota.
- El recurso **es** Cristales de Luz (D15). **PENDIENTE (bloquea implementar, no diseñar):** coste de reanimación y de autorreanimación, Cristales de Luz iniciales y sus fuentes (T10/T11). **Nunca** se vende por Robux.
- *Historial:* hasta el 2026-11-16 los jugadores no morían; se «apagaban» 3 s.

## Enemigos (una especie: la **Sombra**, 8 arquetipos de diseño — ADR-006 D9; prototipo con 3; **sin `Humanoid`**, tope 60 simultáneos)
Arquetipos de diseño (Economía V4.1 §C2): Rastreadora, Acechadora, Bruta, Escupidora, Errante, Subterránea, Cazadora, Vinculadora. Cada uno cambia conducta, aviso de ataque, punto débil y animación, no solo PV y daño. **Correspondencia con los nombres históricos confirmada por D18; los tres forman el prototipo (D9):**
| Arquetipo (nombre histórico) | PV | Velocidad | Daño al faro | Comportamiento | Fase |
|---|---|---|---|---|---|
| Sombra Rastreadora (antes «Sombra») | 20 | 8 | 5/s al contacto | camina recto al faro; débil al foco sostenido | Prototipo |
| Sombra Acechadora (antes «Reptante») | 10 | 14 | 3/s | rápida, llega en grupos y flanquea; vulnerable al terminar el sprint | Prototipo |
| Sombra Bruta (antes «Bruto») | 120 | 4 | 12/s | solo recibe daño pleno con luz de ≥1,5 s seguida (blindaje de cristal se agrieta) | Prototipo |
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
Escalado por nº de jugadores: ×(0,7 + 0,3·n). **Descanso entre noches 25 s** (ajustable 20–30 s tras pruebas; ADR-006 D8; antes 30 s). Solo tras las noches 1–4. Spawn en anillo a radio 60 desde el faro, tope 60 vivos.
Duración objetivo de partida: **10–15 min** (referencia: preparación 20 s, parámetro ajustable hasta 30 s, + noches 480 s + 4 × 25 s + resultados 20 s ≈ 10 min 20 s–10 min 30 s; medir con usuarios).
Columna «Tipos» con los nombres históricos: Sombra = Rastreadora, Reptante = Acechadora, Bruto = Bruta.

## Expedición exterior (MVP, ADR-006 D6)
Una sola expedición o evento exterior **completo** en el MVP: aviso audiovisual y marcador en el minimapa; recompensa en el exterior durante 20–35 s dentro de la noche; Sombras que **persiguen y atacan** al explorador; menos defensores en el faro mientras dura. Opcional e ignorable (se puede ganar sin ella), sin farmeo repetible. La recompensa (p. ej. Cristales de Luz) y la frecuencia las fijan T08/T10. La variedad procedural de eventos se aplaza hasta validar este bucle.

## Cartas permanentes (ADR-006 D1)
Se equipan **antes** de la partida y su capacidad está disponible las 5 noches (activación con enfriamiento o usos; la carta no caduca). **2 ranuras** (hipótesis). Catálogo, efectos y precios: T06/T11. Prototipo **sin** cartas permanentes ni tienda (D13).

## Cartas temporales (elige el equipo 1 de 3 al azar entre las no tomadas; efecto para todo el equipo — ADR-006 D7)
**Votación:** durante el descanso cada jugador vota una de las 3 opciones (cierre 5 s antes de que acabe). Gana la mayoría simple de los votos emitidos; quien no vota se abstiene. **Desempate reproducible:** gana, entre las empatadas, la que aparece primero en el orden de oferta, que genera el servidor con la semilla de la partida; si nadie vota, se aplica la primera de ese orden. En solitario elige el jugador. Nunca se conservan entre partidas ni se venden.
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
Modificadores voluntarios (más Sombras, menos Carga…) con más recompensa en Monedas del Faro (D16); nunca obligatorios.

## Equilibrio objetivo (a medir)
Solo: ~70 % de victoria en N1-3 tras ≥3 partidas, ~35 % partida completa. Cuatro: ~55 %. Medir en playtests.

## Relacionado (añadido en la mejora del vault)
- Índice de enemigos: [[Enemigos]] · Flujo de partida: [[Flujo-de-Jugabilidad.canvas]] · Mapa de diseño: [[Centro-de-Diseno.canvas]]
- Interfaces que muestran estas reglas: [[UI-002-HUD]] · [[UI-003-Seleccion-de-carta]] · [[UI-007-Controles-moviles]]
