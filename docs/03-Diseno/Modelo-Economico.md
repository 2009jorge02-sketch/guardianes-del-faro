---
tipo: diseno
estado: hipotesis (ninguna cifra es resultado ni garantía)
creado: 2026-11-16
---
# Modelo económico

Decisiones: [[ADR-005-estrategia-comercial]], [[ADR-006-contrato-producto-v4]] (D3, D11). Producto: [[Monetizacion]] · [[Progresion-Economia]]. Mercado: [[Mercado-Roblox]] · [[Competidores]]. Etiquetas: **V** verificado en documentación oficial · **H** hipótesis · **C** cálculo.

## 1. Condiciones oficiales (consulta 2026-11-16)
Leídas con herramientas de resumen; las páginas de Creator Hub no muestran fecha. Releer las marcadas ★ antes del primer canje.

| Dato | Valor | Estado |
|---|---|---|
| Tasa DevEx estándar ★ | 0,0038 USD por Robux ganado (30 000 = 114 USD), vigente desde 2025-09-05 | V |
| Tarifa 0,0054 | Solo compras de jugadores de EE. UU. verificados 18+; **no aplica** a España | V |
| Umbral y frecuencia | ≥ 30 000 Robux ganados; una solicitud por mes natural; ≈ 10 días hábiles la primera vez y ≈ 5 después, más el banco | V |
| Elegibilidad | ≥ 13 años, email verificado, portal DevEx, formulario fiscal W-8BEN (individuo) | V |
| Reparto passes y productos ★ | Creador ≈ 70 % (comisión 30 %); la fuente más clara es un anuncio de 2020 | V parcial |
| Retención de fondos | Ventas: 30 días. Creator Rewards: 60 días | V |
| Creator Rewards | Daily Engagement: 5 Robux/día por «gastador activo» (≥ 9,99 USD en 60 días) con ≥ 10 min en la experiencia (una de sus 3 primeras del día). Audience Expansion: 35 % de los primeros 100 USD de un usuario nuevo o reactivado; exige ≥ 100 DAU de media en 60 días. Pago como Robux ganados; alta automática; Roblox puede cambiarlo | V |
| Suscripciones | Robux: 70 % mensual, mínimo 49 Robux, retención ≈ 5 días. Moneda local: 70 % el primer mes y 100 % desde el segundo (verificar), tramos 2,99–14,99 USD, retención 30 días | V parcial |
| Premium Payouts | **Deprecado** desde 2025-07-24; sustituido por Creator Rewards | V |
| Impuestos | W-8BEN generado en la página Taxes de Creator Hub (desde 2026-11-01 ya no por Tipalti). Retención 0–30 % sobre origen EE. UU. según tratado; **24 % si faltan datos válidos**; Form 1042-S anual | V |
| Pendiente | Precio en € de los Robux en España; comisiones concretas de cobro y SEPA; retención del tratado España–EE. UU.; porcentaje de servidores privados de pago | No verificado |

Diferencias frente a [[Politicas-y-Limites]]: Creator Rewards y reparto 70 % pasan de **[PV]** a verificados (parcial); Premium Payouts está deprecado; las ventas entre juegos están desactivadas desde mayo de 2026 (no sirven para promoción cruzada).

## 2. Fórmulas (únicas, usadas en todo el documento)
- `G_m` = Robux gastados en el mes m = `MAU_m × c × a`, con `MAU` = jugadores únicos del mes, `c` = % que compra en el mes, `a` = Robux gastados por comprador y mes.
- `E_m` = Robux ganados = `0,70 × G_m`.
- `EUR_m` = **canjeable bruto** = `E_m × 0,0038 × fx`. **Supuestos base (ADR-006 D11):** `fx = 0,907 €/USD` y `a = 180 R$` por comprador (escenario histórico V4.1); **sensibilidad:** `fx = 0,86` y `a = 250 R$`. Todos son **H**; el tipo real se fija y cita el día del canje. *Las tablas de §3–§4 se calcularon con 0,86 €/USD (`v = 0,003268 €`) y se recalculan en T11 con el simulador Q3.*
- **Ingreso mensual recurrente (MRR)** = `EUR_m` del mes en régimen (aquí, el mes 3).
- **Acumulado** a 30 y 90 días = `EUR_1` y `EUR_1 + EUR_2 + EUR_3`; a 15 días = `0,4 × EUR_1` (**H**: rampa de lanzamiento).
- «Antes de impuestos» = sin retención fiscal ni comisiones de cobro (0–30 % de retención, comisión de cambio 1,9–3 % si se convierte).

## 3. Qué hace falta para 100 € y 300 € al mes (C)
| Objetivo | Robux ganados/mes | Robux gastados/mes |
|---|---|---|
| 100 € | 30 600 (≈ umbral DevEx) | 43 700 |
| 300 € | 91 800 | 131 100 |

Compradores al mes = `G / a`:
| `a` (Robux/comprador·mes) | 100 € | 300 € |
|---|---|---|
| 150 | 291 | 874 |
| 300 | 146 | 437 |
| 500 | 87 | 262 |
| 1 000 | 44 | 131 |

Jugadores únicos al mes con `a = 300`: **100 €:** 14 600 (c = 1 %), 7 300 (2 %), 4 900 (3 %). **300 €:** 43 700, 21 900, 14 600. Con `c = 2 %` y `a = 350` bastan ≈ 6 200 (100 €) y ≈ 18 700 (300 €) jugadores únicos al mes.

## 4. Escenarios (H; ilustran la fórmula, no predicen)
Retención anclada a una medición de terceros (mediana D1/D7/D30 10,3 % / 1,6 % / 0,5 %; 1 % superior 22,2 % / 9,1 % / 4,7 %; fecha y muestra poco claras). Los benchmarks propios de Creator Hub la sustituirán.

| | Conservador | Central | Optimista |
|---|---|---|---|
| Retención D1/D7/D30 | 10 % / 1,6 % / 0,5 % | 15 % / 4 % / 1,5 % | 22 % / 9 % / 4,7 % |
| `MAU` mes 1 / 2 / 3 | 800 / 700 / 600 | 3 500 / 4 000 / 3 500 | 25 000 / 40 000 / 35 000 |
| `c` y `a` | 1 %, 250 | 2 %, 350 | 3 %, 450 |
| Robux gastados (90 d) | 5 250 | 77 000 | 1 350 000 |
| Robux ganados (90 d) | 3 675 | 53 900 | 945 000 |
| **Canjeable acumulado 15 d** | ≈ 2 € | ≈ 22 € | ≈ 309 € |
| **Canjeable acumulado 30 d** | ≈ 5 € | ≈ 56 € | ≈ 772 € |
| **Canjeable acumulado 90 d** | ≈ 12 € | ≈ 176 € | ≈ 3 088 € |
| **MRR en el mes 3** | ≈ 3 € | ≈ 56 € | ≈ 1 081 € |

Lectura: **el escenario central no alcanza 100 €/mes** (MRR ≈ 56 €); necesitaría ≈ 6 200 jugadores únicos al mes con esos `c` y `a`. El optimista equivale a un éxito atípico: no es base de planificación. En el central, los Robux ganados superan 30 000 hacia el día ~50 y, con retención de 30 días, el primer canje solo sería posible hacia el día ~80, con cobro semanas después (H).

## 5. Qué parte del gasto llega al creador (H)
Si el jugador paga ≈ 0,011 €/Robux (**no verificado**), el creador percibe ≈ 21 % de lo gastado (70 % × 0,003268/0,011). Para 300 €/mes los jugadores gastarían ≈ 1 400 €. Solo sirve para estimar el gasto de los jugadores; el canjeable no depende de ese precio.

## 6. KPI de éxito (sustituyen a las visitas)
- **Experiencia:** abandono en la primera partida, % que repite partida, duración de sesión, D1/D7/D30 frente al benchmark de «experiencias similares» de Creator Hub, móvil/PC, solitario vs cooperativo.
- **Monetización:** % de compradores (`c`), ingreso por usuario, ingreso por comprador (`a`), conversión por producto, compras repetidas, Robux ganados por periodo, distancia al umbral de 30 000.
- **Rentabilidad:** MRR frente a ingresos puntuales, horas de mantenimiento por mes, coste real de producción y promoción, relación esfuerzo/retorno, dependencia de actualizaciones.

## 7. Puerta comercial (propuesta para [[ROADMAP]])
Tras el Beta, ampliar la monetización solo si: D1 ≥ mediana del benchmark propio, `c` ≥ 1 % y `a` ≥ 250 en jugadores reales, y el embudo de [[Adquisicion-Organica]] aporta jugadores a un coste de tiempo asumible. Los umbrales salen de este modelo (H) y se recalibran con datos reales.
