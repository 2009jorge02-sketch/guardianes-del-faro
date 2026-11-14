---
tipo: planificacion
estado: plan (ninguna prueba realizada todavía)
creado: 2026-11-14
---
# Plan de validación del prototipo

Decide si **Guardianes del Faro** merece seguir. No hay resultados todavía: todo lo de abajo son **criterios por cumplir**. Contexto: [[Revision-Concepto]], [[MVP]] (Puerta 1), [[Rendimiento]], [[Riesgos]] (R1–R3).

## 1. Objetivos
Validar tres incertidumbres ([[Revision-Finalistas]]): **(1)** el haz es divertido; **(2)** rinde en móvil de gama baja; **(3)** hay motivo para repetir. Más: cooperar aporta valor y el control táctil funciona.

## 2. Muestra y método (honesto con lo pequeño)
Muestra pequeña ⇒ **señal cualitativa, no estadística**. Mínimo **5 testers ajenos al proyecto** (≥2 con móvil, ≥2 con PC), cada uno ≥2 partidas; **observar sin ayudar** y anotar. Medición con herramientas de [[TASK-012]] y registro en `docs/07-Registro/Revisiones/playtest-AAAA-MM-DD.md`. Se justifica 5 porque la mayoría de problemas de usabilidad aparecen con pocos usuarios; no sirve para estimar retención real (eso es Beta).

## 3. Diversión
Señales observables (no inventar números previos): 
- Entienden qué hacer **sin explicación** en <30 s.
- Tiempo hasta el primer enemigo destruido <20 s.
- ≥4 de 5 terminan la primera noche; ≥3 de 5 **piden/aceptan una segunda partida sin que se les insista** (pregunta directa y observación).
- Comentarios espontáneos positivos sobre el haz (anotar literal) vs. aburrimiento (mirar el móvil, abandonar).
- Preguntas post-partida (1–5): «¿Fue divertido apuntar?», «¿Qué hiciste que fuera tu decisión?».
Umbral 3 de 5: justificación — equivale a mayoría simple de una muestra mínima; si <2, es señal fuerte de problema.

## 4. Rejugabilidad
- Partidas completas por tester en una sesión de 30 min (¿repiten por voluntad propia?).
- Tras 3 partidas: ¿notan diferencias entre ellas? (pregunta abierta) y ¿probaron estrategias distintas con las cartas? (con MVP).
- Nunca medir con incentivos externos; el tester decide cuándo parar.
- D1/D7 reales solo en Beta ([[ROADMAP]]); aquí no se afirma retención.

## 5. Cooperación
Comparar 2–4 jugadores vs. 1: ¿hay momentos de coordinación espontánea (cruce de haces, uso del Foco)? ¿Se quejan de molestar a otros? Señal positiva: ≥3 de 5 grupos describen un momento cooperativo concreto. Comprobar también que jugar **solo** es satisfactorio.

## 6. Rendimiento (técnico)
Con [[TASK-012]]: FPS medio y mínimo, ping y tiempo de servidor con 50/100/200 enemigos; objetivo del diseño **≥30 FPS en móvil de gama baja con 60 enemigos y 4 jugadores** (ver [[Rendimiento]]; el objetivo oficial de Roblox es **[PV]**, el umbral es propio y se justifica por ser el mínimo habitual de fluidez jugable). Registrar modelo de dispositivo. Si falla: bajar tope o activar opción B de [[ADR-003-enemigos]].

## 7. Multiplataforma
- **PC:** ratón + teclado; comprobar legibilidad y precisión.
- **Móvil real** (mínimo un teléfono de gama baja y uno medio, el usuario los aporta): comparar **control táctil A (arrastrar = apuntar y encender)** vs **B (botón + arrastre)** con los mismos testers alternando el orden; medir tasa de «no puedo apuntar» (observada), comodidad (1–5) y FPS.
- Emulador de Studio **no sustituye** al dispositivo real.

## 8. Criterios de decisión
| Resultado | Condición (todas las de la fila) |
|---|---|
| **Continuar** | Rendimiento cumple (o con tope ajustado documentado); ≥3/5 repiten voluntariamente; ≥4/5 terminan noche 1; sin bloqueo táctil (móvil comodidad ≥3/5 medio) |
| **Modificar elementos importantes** | Rendimiento falla pero tiene arreglo (tope/ADR-003 B); o diversión 2/5 con comentarios que señalan causas concretas (monotonía, control, dificultad); o táctil insuficiente → rediseñar control/enemigos/cartas y repetir validación (máx. 2 ciclos) |
| **Descartar y reconsiderar** | Tras 2 ciclos de ajustes sigue <2/5 repetirían; **o** rendimiento inviable incluso con tope 30 y opción B; **o** fallo de diversión fundamental y sin hipótesis de arreglo. Alternativas: Horda de Cristal (base técnica), Pastelería Fantasma ([[Ideas-Evaluadas]]) |

## 9. Ejecución
Fase 1 termina con una sesión de playtest preparada por Claude (guion y formulario en el registro) y ejecutada por el usuario. Claude analiza resultados y registra la decisión en un ADR. Nada de esto se da por hecho hasta existir el registro.
