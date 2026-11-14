---
tipo: gdd
juego: Guardianes del Faro (provisional)
version: 0.1
estado: borrador completo — fuente de verdad del diseño
actualizado: 2026-11-14
---
# Game Design Document

Visión: [[Concepto]] · [[Pilares]] · Decisión: [[ADR-001-concepto]]. Las cifras de balance viven **solo** en [[Mecanicas]] (y luego en `Config` del código).

## 1. Resumen
Cooperativo 1–4 jugadores. 5 noches (~10 min). Se defiende el **Faro** (Integridad) de **Sombras** de cristal apuntando luz. Entre noches, cada equipo elige una **carta de mejora**. Al terminar se obtienen **Luz (XP de cuenta)** y **Cristales (moneda blanda)** para desbloquear cosméticos y variantes laterales.

## 2. Primera partida, paso a paso (jugador nuevo)
1. Pulsa Jugar; en <20 s aparece en la isla al atardecer (sin menú largo).
2. Prompt contextual: «Mantén pulsado para encender la linterna» (táctil: botón; PC: clic). Aparecen 3 Sombras lentas.
3. Al destruir la primera: destello, sonido y +1 contador. Segundo prompt: «Sube al Foco Mayor» (opcional).
4. Noche 1 (75 s) sube en intensidad; el Faro recibe un daño leve (se ve y se oye).
5. Intermedio de 30 s: **3 cartas**, elige 1 (votación simple o el primero que elija en solitario).
6. Noches 2–5; la 5.ª termina con la **Marea Negra** (jefe grande) — en el prototipo, simplemente oleada final.
7. Pantalla de resultados: noches superadas, Sombras destruidas, Cristales y Luz ganados, botón «Otra partida».

## 3. Bucle principal
**Entrar → luchar la noche (apuntar luz) → mejora de carta → siguiente noche → resultado → recompensa de cuenta → desbloquear/equipar cosmético → nueva partida.**
Motivos para volver (sin manipulación): maestría del haz, builds distintos con cartas, dificultades «Tormenta» opcionales, cosméticos por logros, jugar con amigos. **No** hay rachas diarias con castigo, ni temporizadores de espera, ni cuenta atrás con ofertas.

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
- **Derrota:** Integridad = 0. Los jugadores **no mueren** (se «apagan» 3 s); no hay eliminación.

## 6. Alcance por fase
Prototipo y MVP: [[MVP]]. Alfa/Beta/Lanzamiento y actualizaciones: [[ROADMAP]].

## 7. Fuera de alcance (hasta validar el núcleo)
Exploración diurna, inventario, trading, PvP, azar de pago, múltiples islas (solo tras MVP), chat propio.

## 8. Cuestiones abiertas
Nombre definitivo · número de jugadores máximo (4 propuesto) · si el jefe entra en MVP o Alfa · tono de audio. Registradas en [[Riesgos]].
