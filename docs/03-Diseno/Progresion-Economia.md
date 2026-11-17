---
tipo: diseno
estado: valores iniciales; recursos redefinidos por ADR-006 (D2)
actualizado: 2026-11-17
---
# Progresión y economía

Ver [[GDD]], [[Monetizacion]], [[ADR-006-contrato-producto-v4]]. Principio: **la progresión da variedad, opciones estratégicas y expresión; las cartas permanentes amplían estrategias sin invalidar a quien juega gratis** (una legendaria no puede dar por sí sola un margen de daño o defensa que haga inútil a otro jugador).

## Recursos (D2)
| Recurso | Ámbito | Se obtiene | Sirve para |
|---|---|---|---|
| **Experiencia de Guardián (XP)** (antes «Luz», D17) | Permanente | Por partida: 20 por noche superada + 1 por 10 Sombras + 50 por victoria | Niveles de cuenta 1–50; recompensas no cosméticas (D16) |
| **Monedas del Faro** | Permanente | **Hipótesis V0.1 para simulación:** 100 por noche superada + 500 por victoria (≈ 1 000 por victoria); derrota = solo noches superadas; bonus de eventos con tope | Desbloquear cartas permanentes (alternativa a Robux, misma carta) |
| **Cristales de Luz** | **Solo dentro de una partida** (no persisten) | En la partida: eventos/expediciones exteriores | Reanimación (D15) y defensa del faro; saldo compartido del equipo. Coste y fuentes exactas: [[Mecanicas]] |
Sin tope diario, sin energía, sin cooldowns. Las Monedas del Faro **no** se venden (vender monedas trivializaría el doble precio); los Cristales de Luz nunca se venden. El tope heredado de 80 Cristales por partida **no** se aplica a las Monedas del Faro.

**Cuestiones abiertas (ADR-006):** (1) los hitos de nivel de abajo dan cosméticos gratis, lo que choca con «cosméticos solo Robux» (D10) — decidir si se sustituyen por recompensas no cosméticas o se admite una excepción; (2) «Luz» (XP) y «Cristales de Luz» se confunden: valorar un renombrado.

## Niveles de cuenta (ejemplo)
Nivel n requiere 100 + 25·n de XP. Ritmo objetivo: nivel 10 en ~8–10 partidas. Hitos (D16; valores en T11): Monedas del Faro extra, progresión de cartas y variantes jugables gratuitas (p. ej. lvl 10 variante de linterna). *Historial: lvl 3 skin de linterna, 5 color del haz, 20 skin de faro, 30 mascota, 50 título.*

## Variantes laterales de linterna (no mejoran el poder total)
- *Linterna estándar*: cono 35°, alcance 28.
- *Foco estrecho*: cono 20°, alcance 36, daño +25 % (precisión).
- *Lámpara ancha*: cono 55°, alcance 20, daño −25 % (control de multitudes).
Presupuesto de poder equivalente, validado por simulación en Beta.

## Fuentes y sumideros
Fuente única de Monedas del Faro: partidas. Sumidero: cartas permanentes (precios provisionales en [[Monetizacion]] §Cartas permanentes). Sin trading, sin economía entre jugadores → sin inflación ni estafas a menores. Objetivos de diseño (Q3, T11): primera común en ≤ 10 partidas; primera legendaria en ≈ 12–20 h de juego gratis de un perfil habitual (D4). Con la V0.1 la legendaria saldría ≈ 41–58 h a 50 % de victorias (estimación de [[REV-T00-2026-11-17]]): **la V0.1 no cumple D4** y T11 debe recalibrarla.

## Hipótesis a validar (R3 en [[Riesgos]])
¿La maestría + cosméticos bastan para D1/D7? Medir con analítica propia en Beta ([[Rendimiento]]).

## Refuerzo de progresión (aprobado en dirección; solo lo marcado MVP entra en el MVP)
Objetivo: dar metas más allá de las primeras partidas sin poder neto ni presión ([[ADR-005-estrategia-comercial]]). Valores iniciales a probar en Beta.
| Elemento | Fase | Notas |
|---|---|---|
| Hito de recompensa (Monedas del Faro o progreso de carta) cada 3–5 partidas al inicio (D16) | MVP | Ajustar la tabla de hitos de arriba; sin cambio de mecánica |
| Maestrías por variante de linterna (logros que dan Monedas del Faro) | Alfa | Premian dominar el haz |
| Desafío semanal opcional, **sin rachas ni castigo** | Alfa | Sin temporizadores de oferta |
| Dificultades «Tormenta» con recompensa en Monedas del Faro | Alfa | Ya previstas en el GDD |
| Bonus cooperativo de Monedas del Faro (jugar con amigos) | Alfa | Refuerza el co-juego |
| Rangos del Guardián más allá del nivel 50 (recompensas no cosméticas, D16) | Beta, solo si la retención lo pide | No ampliar antes |

*Historial (2026-11-16, sustituido por D2/D10):* una partida daba como máximo 80 Cristales (moneda blanda) para comprar cosméticos de 100–1 500. Los cosméticos pasan a ser solo Robux y los Cristales de Luz a recurso de partida.
