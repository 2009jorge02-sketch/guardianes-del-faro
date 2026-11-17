---
tipo: diseno
estado: contrato V4.1 (ADR-006); diseño aprobado, implementación tras validar el prototipo (ADR-004); ningún ingreso está garantizado
actualizado: 2026-11-17
---
# Monetización

Base normativa: [[Politicas-y-Limites]]. Objetivo, fórmulas y condiciones oficiales de DevEx, Creator Rewards y suscripciones: [[Modelo-Economico]]. Decisiones: [[ADR-005-estrategia-comercial]] y [[ADR-006-contrato-producto-v4]] (que sustituye el antiguo principio «solo cosmética»).

## Principios (ADR-006)
1. **Cartas permanentes por dos vías con función idéntica:** se desbloquean con Monedas del Faro (jugando) **o** con Robux. Ninguna versión de pago es más fuerte; ninguna ventaja es imposible de conseguir gratis (D1).
2. **Cosméticos desbloqueables solo por Robux** (D10/D16); los aspectos y el equipamiento básicos son gratuitos. No cambian estadísticas, colisiones, visión ni hitboxes.
3. **Prohibido:** vender reanimaciones o el recurso raro de la partida (D5), pagar por saltar noches, azar de pago (cajas/huevos/llaves), ofertas con temporizador, escasez artificial, ventanas emergentes repetidas, ofertas para «salvar» una partida en curso.
4. Precios visibles en Robux y en Monedas del Faro, iguales en la tienda y en la ventana de compra; precios regionales dinámicos (Managed Pricing), nunca fijados a mano en la UI.
5. Transparente y apto para menores (Mild). Los contadores y ofertas deben ser exactos (Roblox lo exige).
6. Prototipo **sin tienda real, sin pagos y sin persistencia comercial** (D13, [[ADR-004-validacion-concepto]]).

*Historial:* hasta el 2026-11-16 el principio 1 era «solo cosmética y comodidad no competitiva»; la Investigación Comercial V4.1 lo recomendaba. Queda como contexto (D12).

## Cartas permanentes — precios provisionales SOLO para simulación (D3)
Rareza: Monedas del Faro / Robux. Común 6 000 / 29 · Poco común 15 000 / 59 · Rara 35 000 / 99 · Épica 70 000 / 179 · Legendaria 140 000 / 299. **No son precios:** T11 los recalibra con el simulador Q3 (primera común en ≤ 10 partidas; primera legendaria en ≈ 12–20 h, D4).

## Cosméticos — tabla provisional única (Economía V4.1 §B2, D10)
| Producto | Precio de referencia (R$) |
|---|---|
| Colores/variantes de linterna | 19–49 |
| Efectos de haz y partículas | 49–99 |
| Emblemas, banderas, muebles | 39–119 |
| Aspectos integrales del faro | 129–249 |
| Packs temáticos premium | 299–499 |
Faro compartido: la regla de qué aspecto se muestra con varios propietarios se define antes de producirlo (T06/T11).

## Productos históricos (2026-11-16; sustituidos por la tabla anterior, se conservan como referencia)
| Producto | Tipo | Contenido | Precio inicial (H) |
|---|---|---|---|
| «Chispa» | Developer product | Un color de haz o efecto menor | 49–99 Robux |
| Pack «Linterna» | Developer product / pase | Skin de linterna + efecto | ≈ 199 |
| Pack «Mascota guardiana» | Developer product / pase | Acompañante cosmético | ≈ 299 |
| Pack «Faro» | Developer product / pase | Conjunto de skins de faro + haz | ≈ 399 |
| Pase «Farero» | Game pass | Skins exclusivas de faro y haz, título; sin ventaja de poder | ≈ 599–799 |
| «Apoya al faro» | Developer product | Donación opcional sin beneficio mecánico | libre, bajo |
| Servidor privado | Función de Roblox | Partidas con amigos | según Roblox |

**Escalera de precios:** una compra de entrada barata, varias intermedias y un pase. Objetivo de diseño: que un comprador haga 2–4 compras pequeñas en lugar de una (escenario base 180 R$/comprador, sensibilidad 250 R$; D11, [[Modelo-Economico]]). Se mide la conversión de cada escalón.

## Visibilidad de los productos
Los cosméticos se ven en la partida (haz y linterna del equipo, mascota, faro) y en una vitrina del lobby con vista previa, precio visible y sin cuentas atrás. Texto de oferta honesto: no decir «agotándose» ni «temporal» si no lo es; los eventos estacionales recuperables se anuncian como tales.

## Creator Rewards
Daily Engagement exige ≥ 10 min de juego de un gastador activo; las partidas de ~10 min lo permiten, **sin diseñar el juego en torno a ello**. Audience Expansion necesita ≥ 100 DAU de media. Roblox puede cambiar el programa: no es ingreso base ([[Modelo-Economico]] §1).

## Monetización recurrente (fase posterior, no aprobada)
Suscripción «Guardián» y aceleradores: decisiones abiertas con ventajas, riesgos y costes en [[Decisiones-Monetizacion-Pendientes]]. Se decide tras la puerta comercial del [[ROADMAP]].

## Analítica comercial
Eventos mínimos: entra y juega, completa noche 1, segunda partida, abre tienda, vista y compra por producto. Detalle del embudo en [[Adquisicion-Organica]] §6.

## Descartado
«Doble XP» (presiona a niños en cooperativo), cajas o gacha de pago, acceso de pago, ofertas con temporizador, reanimaciones o recursos de partida por Robux, cartas temporales de pago.

## Hipótesis comerciales (no resultados)
Los líderes del género ganan millones al mes (estimación de terceros, [[Competidores]]); la mediana de un juego nuevo es mucho menor. Con las hipótesis de [[Modelo-Economico]] §4 el escenario central queda por debajo de 100 €/mes; alcanzarlo exige más audiencia o gasto por comprador. Primer hito económico real: 30 000 Robux ganados para el primer canje.
