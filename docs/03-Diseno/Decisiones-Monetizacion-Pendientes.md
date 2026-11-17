---
tipo: decision-pendiente
estado: abiertas (ninguna aprobada)
creado: 2026-11-16
---
# Decisiones de monetización pendientes

Origen: [[ADR-005-estrategia-comercial]] §5. Hasta que el usuario decida, **no** se vende Cristales, **no** hay aceleradores y **no** hay suscripción. Base: [[Monetizacion]] · [[Modelo-Economico]] · [[Politicas-y-Limites]]. Costes de implementación: estimación relativa para Codex (S pequeño, M medio, L grande), no medida.

> **Actualización 2026-11-17 ([[ADR-006-contrato-producto-v4]]):** D1 queda **superada**: los Cristales de Luz pasan a ser un recurso solo de partida y nunca se venden; la moneda permanente (Monedas del Faro) tampoco se vende. D2 y D3 siguen **abiertas**. Lo que sigue de D1 se conserva como historial.

## D1 · Vender Cristales por Robux
| | |
|---|---|
| Qué es | Producto de desarrollador que da Cristales (moneda blanda que ya se gana jugando) para comprar cosméticos desbloqueados |
| Ventajas | Compra flexible y repetible; amplía los precios; permite packs pequeños |
| Riesgos | Contradice «Robux directos, sin monedas intermedias» ([[Monetizacion]]) y oscurece el precio real; presión sobre menores; exige equilibrar bien la economía gratuita; sin azar no activa las normas de ítems aleatorios |
| Coste | M: producto, recibo, persistencia segura y validación en servidor ([[Seguridad]]) |
| Recomendación | **Esperar al Beta.** Con la escalera de cosméticos en Robux directos se mide la conversión sin moneda intermedia |

## D2 · Aceleradores de progresión («doble de Cristales», ayuda de Luz)
| | |
|---|---|
| Qué es | Pase que multiplica la ganancia de Monedas del Faro o XP (antes «Cristales o Luz»; con ADR-006 afectaría al ritmo de cartas: revisar riesgo de pagar por poder) |
| Ventajas | Es un pase habitual en el género; ingreso repetible con poco contenido |
| Riesgos | Se descartó «Doble XP» por presionar a niños en cooperativo ([[GDD]]); puede empeorar la experiencia gratuita si se frena la progresión para venderlo; reputación |
| Coste | S–M: multiplicador en servidor; lo delicado es equilibrar |
| Recomendación | **No antes de medir la progresión gratuita.** Si se aprueba, la ruta gratuita debe seguir siendo satisfactoria y el pase no cambia el poder |

## D3 · Suscripción (p. ej. «Guardián»)
| | |
|---|---|
| Qué es | Suscripción en Robux (70 % cada mes, mínimo 49 Robux, retención ≈ 5 días) o en moneda local (70 % el primer mes y 100 % después, tramos 2,99–14,99 USD, retención 30 días; verificar), con cosmético mensual y comodidad |
| Ventajas | Único ingreso verdaderamente **recurrente** y previsible |
| Riesgos | Obliga a entregar valor cada mes (mantenimiento); con pocos suscriptores no compensa el trabajo; hay que cumplir las normas de transparencia y cancelación |
| Coste | M técnico (producto, comprobación de estado, entrega mensual); L en trabajo continuo de contenido |
| Recomendación | **Tras la puerta comercial** ([[Modelo-Economico]] §7) y solo con un ritmo de contenido sostenible |

## Cómo decidir
Presentar cada decisión con datos del Beta: `c`, `a`, compras repetidas, retención y quejas. El usuario aprueba o rechaza cada una por separado y se registra en un ADR.
