---
tipo: investigacion
tema: Políticas de monetización, seguridad de menores, límites técnicos y herramientas
fecha_consulta: 2026-11-14
autor_agente: subagente Sonnet medium (equivalente a market-researcher)
confianza: media
---
# Políticas, límites técnicos y herramientas de Roblox

> Datos obtenidos con WebFetch/WebSearch, que devuelven resúmenes. Lo marcado **[PV]** está *pendiente de verificación* en la página original antes de usarlo en decisiones económicas. Ver [[Fuentes]], [[Monetizacion]], [[ARCHITECTURE]].

## Monetización
| Dato | Valor | Fuente | Estado |
|---|---|---|---|
| Vías oficiales | immersive ads, Roblox Plus, suscripciones, game passes, developer products, acceso de pago, servidores privados, ítems de catálogo, Creator Store | create.roblox.com/docs/production/monetization | Verificado |
| Retención de ventas | 30 días (escrow) | idem | Verificado |
| Reparto de Robux gastados en la experiencia | creador ≈70 % (resumen de búsqueda) | create.roblox.com/docs/monetize | **[PV]** |
| Tarifa DevEx estándar | 0,0038 USD/Robux (~114 USD por 30.000) | .../developer-exchange | Verificado |
| Tarifa DevEx 18+ EE. UU. | 0,0054 USD/Robux desde 2026-06-08 | .../18-plus-devex-rate | Verificado |
| Requisitos DevEx | ≥13 años, ≥30.000 Robux ganados, email verificado, portal DevEx, W-9/W-8 | .../developer-exchange | Verificado |
| Creator Rewards | sustituye afiliados; Daily Engagement 5 Robux/día; Audience Expansion 35 % de las primeras 100 USD | create.roblox.com/docs/creator-rewards | **[PV]** |

## Ítems aleatorios de pago y menores
- Obligatorio mostrar **todos los resultados y sus probabilidades reales en %**, también en compras indirectas (llaves, tickets, moneda comprada con Robux). Modificadores de suerte deben explicarse antes de comprar. Fuente: .../paid-random-items.
- Consultar `PolicyService:GetPolicyInfoForPlayerAsync()`: si `ArePaidRandomItemsRestricted` es true, ofrecer alternativa (ruta gratuita, compra directa o bloqueo). `IsPaidItemTradingAllowed` controla el intercambio.
- Etiquetas de madurez: Minimal, Mild, Moderate, Restricted (18+ con age check). Age check obligatorio para chat desde enero 2026 en regiones con chat. Cuentas Kids 5–8 y Select 9–15. **[PV]** en docs oficiales.
- Community Standards: página devolvió 403 → **[PV]**.

**Decisión de diseño derivada:** el juego no usará cajas aleatorias de pago (ver [[Monetizacion]]); así se evita todo el régimen de divulgación y restricción por edad.

## Límites técnicos
- DataStore: valor máx. 4 194 304 caracteres; nombre/clave/scope ≤50 caracteres; presupuesto por servidor 60 + jugadores×40 (lectura y escritura) por minuto. Fuente: .../data-stores/error-codes-and-limits.
- Texturas: memoria ∝ píxeles (1024² = 4×512²); recomendado ≤512×512 (menores <256). Streaming: bajar `StreamingMinRadius`/`StreamingTargetRadius`. Fuente: .../performance-optimization/improve.
- **[PV]**: objetivos concretos de FPS/memoria móvil, jugadores máx. por servidor, tamaño de mapa.
- Seguridad cliente-servidor: no verificado en docs; principio asumido: el servidor valida todo.

## Herramientas (releases consultadas 2026-11-14)
| Herramienta | Versión | Fecha |
|---|---|---|
| Rojo | 7.7.1 | 2-oct (año no mostrado) |
| StyLua | 2.6.0 | 2026-10-10 |
| Selene | 0.32.0 | 2026-10-01 |
| luau-lsp | 1.70.1 | 2026-09-27 |

Roblox Studio incluye servidor **MCP integrado** (Assistant → Manage MCP Servers) compatible con Claude Code/Desktop; compatibilidad con Codex **[PV]**. Fuente: create.roblox.com/docs/studio/mcp (resumen).
