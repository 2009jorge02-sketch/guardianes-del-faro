---
tipo: gdd
juego: Guardianes del Faro (provisional)
version: 0.3
estado: borrador completo — fuente de verdad del diseño (contrato V4.1, ADR-006)
actualizado: 2026-11-17
---
# Game Design Document

Visión: [[Concepto]] · [[Pilares]] · Decisiones: [[ADR-001-concepto]], [[ADR-006-contrato-producto-v4]]. Las cifras de balance viven **solo** en [[Mecanicas]] (y luego en `Config` del código). Guía estética: [[Indice-Referencias-Visuales]] (las imágenes no fijan reglas).

## 1. Resumen
Cooperativo 1–4 jugadores. 5 noches (10–15 min). Se defiende el **Faro** (Integridad) de la **Sombra** (una especie, varios arquetipos) apuntando luz. Durante las noches puede aparecer una **expedición exterior** arriesgada. Tras las noches 1–4 el equipo vota una **carta temporal**. Antes de jugar se equipan **cartas permanentes** (Monedas del Faro o Robux, misma carta). Al terminar se obtienen **Experiencia de Guardián (XP)** y **Monedas del Faro**. Los **Cristales de Luz** son un recurso solo de la partida ([[Progresion-Economia]] §Recursos).

## 2. Primera partida, paso a paso (jugador nuevo)
1. Pulsa Jugar; en <20 s aparece en la isla al atardecer (sin menú largo).
2. Prompt contextual: «Mantén pulsado para encender la linterna» (táctil: botón; PC: clic). Aparecen 3 Sombras lentas.
3. Al destruir la primera: destello, sonido y +1 contador. Segundo prompt: «Sube al Foco Mayor» (opcional).
4. Noche 1 (75 s) sube en intensidad; el Faro recibe un daño leve (se ve y se oye).
5. Descanso de 25 s: **3 cartas temporales**, el equipo vota 1 (en solitario decide el jugador; desempate en [[Mecanicas]]).
6. Noches 2–5; la 5.ª termina con la **Marea Negra** (jefe grande) — en el prototipo, simplemente oleada final.
7. Pantalla de resultados: noches superadas, Sombras destruidas, Monedas del Faro y Experiencia de Guardián ganadas, botón «Otra partida».

## 3. Bucle principal
**Equipar cartas permanentes → luchar la noche (apuntar luz; expedición opcional; rescatar compañeros) → votar carta temporal → siguiente noche → resultado → Monedas del Faro y XP → desbloquear cartas permanentes → nueva partida.**
Motivos para volver (sin manipulación): maestría del haz, builds distintos con cartas, dificultades «Tormenta» opcionales, recompensas por logros, jugar con amigos. **No** hay rachas diarias con castigo, ni temporizadores de espera, ni cuenta atrás con ofertas.

## 4. Sistemas (detalle en otros documentos)
| Sistema | Documento |
|---|---|
| Reglas, controles, enemigos, cartas, números | [[Mecanicas]] |
| Progresión, recompensas, economía | [[Progresion-Economia]] |
| Monetización ética | [[Monetizacion]] |
| Mapa/isla | [[Mapas]] |
| Arte, UI, audio | [[Arte-UI-Audio]] |
| Experiencia, dificultad, accesibilidad | [[Experiencia-Jugador]] |
| Técnica | [[ARCHITECTURE]] |

## 5. Condiciones de victoria/derrota
- **Victoria:** Faro con Integridad >0 al terminar la noche 5.
- **Derrota:** Integridad = 0, o en solitario el jugador eliminado sin recurso para autorreanimarse.
- **Jugadores:** tienen salud, pueden ser **derribados**, **rescatados** por compañeros o **eliminados**; la estación de reanimación consume un recurso raro compartido que también sirve para defender el faro ([[Mecanicas]] §Salud; ADR-006 D5). *Historial: hasta v0.2 los jugadores no morían.*

## 5.1 Gates de calidad Q1–Q4
Personas reales (Q1), arte verificado en Roblox (Q2), simulador económico (Q3) y recuperación probada (Q4), con umbrales en [[ADR-006-contrato-producto-v4]] §Gates. Estado: **NOT_VERIFIED** los cuatro.

## 6. Alcance por fase
Prototipo y MVP: [[MVP]]. Alfa/Beta/Lanzamiento y actualizaciones: [[ROADMAP]].

## 7. Fuera de alcance (hasta validar el núcleo)
Exploración diurna, trading, PvP, azar de pago, múltiples islas (solo tras MVP), chat propio, variedad procedural masiva de eventos/jefes (tras validar la primera expedición, D6). La expedición exterior nocturna **sí** entra en el MVP.

## 8. Cuestiones abiertas
Nombre definitivo · número de jugadores máximo (4 propuesto) · si el jefe entra en MVP o Alfa · tono de audio. Registradas en [[Riesgos]].

## 9. Objetivos comerciales y retención
Decisión: [[ADR-005-estrategia-comercial]]. Cifras y fórmulas solo en [[Modelo-Economico]].
- **Objetivo:** 100–300 €/mes canjeables (DevEx) antes de impuestos, con potencial de superarlos; meta comercial, no previsión. El éxito se mide por retención y monetización, no por visitas.
- **Primer minuto:** jugar en <20 s y destruir la primera Sombra en <20 s (§2) son palancas de retención; invitar a amigos con un clic.
- **Visibilidad:** haz, linterna, faro y mascota del equipo se ven en partida; vitrina de la tienda en el lobby ([[Monetizacion]]).
- **Progresión de largo plazo:** [[Progresion-Economia]] §Refuerzo de progresión.
- **Analítica comercial mínima** (embudo) desde el MVP: [[Adquisicion-Organica]] §6.
- **Monetización (ADR-006):** cartas permanentes por Monedas del Faro o Robux con función idéntica; cosméticos solo Robux; nunca reanimaciones ni recursos de partida por Robux ([[Monetizacion]]). Se implementa después de validar el prototipo (ADR-004). Aceleradores y suscripción siguen sin aprobar ([[Decisiones-Monetizacion-Pendientes]]).
