---
tipo: diseno
tema: Revisión final del concepto provisional (game-director)
fecha: 2026-11-14
estado: concepto provisional aprobado por el usuario para validar un prototipo
autor: Sonnet 5.5 medium (conversación principal, skill game-director)
---
# Revisión del concepto — Guardianes del Faro

El usuario aprobó el concepto **solo como provisional**, para validar un prototipo ([[VALIDACION-PROTOTIPO]]). No se repite la investigación ([[Mercado-Roblox]]) ni la revisión de Opus ([[Revision-Finalistas]]). Todo lo siguiente son **hipótesis de diseño** hasta jugar el prototipo.

## 1. Diversión de la mecánica principal
**Qué la haría divertida**
- **Precisión con margen:** el cono de 35° perdona pequeños errores, pero premia barrer rápido (las Sombras no iluminadas son +25 % más rápidas). Tensión: *iluminar = controlar*.
- **Estado de flujo:** gestión de la Carga (≈8 s de luz continua y recarga) crea ritmo de ráfagas y pausas, no un clic mantenido infinito.
- **Respuesta inmediata:** el primer feedback (haz, chispa, tono) en el mismo frame; sin ello el pilar 1 ([[Pilares]]) falla.
- **Satisfacción de multitud:** barrer un grupo y verlo romperse en cristales con un único gesto.

**Qué podría volverlo aburrido (riesgos)**
1. **Un solo verbo repetido** («mantén pulsado y gira») durante 10 min.
2. **Enemigos que solo caminan recto:** sin amenazas distintas la decisión es nula.
3. **Cooperación decorativa:** si cada jugador hace lo mismo en paralelo, el multijugador no aporta.
4. **Dificultad plana o picos injustos.**

**Mejoras concretas (bajo coste, para prototipo/MVP)**
- **Daño por concentración** (ya parcial): el Bruto exige luz sostenida de 1,5 s → decide *a quién* apuntar.
- **Mecánica de «cruce de haces»:** donde dos conos se solapan, el daño ×1,5 (es matemática de cono, barato) → cooperación real y visible. *Propuesta para TASK-006 como parámetro `overlapBonus` desactivado por defecto; activarlo y probarlo en playtest.*
- **Variedad de amenaza ya en MVP:** Reptante (flanqueo rápido) y Bruto; **Gaviota** (aérea, ataca la lámpara) pasa de Alfa a «candidata MVP» si el prototipo se siente repetitivo.
- **Foco Mayor como decisión de riesgo/recompensa:** daño alto pero te aleja del suelo.
- **Ritmo de noche:** oleadas en 2–3 «pulsos» con respiro de 3–5 s (permite recargar y leer) en lugar de un flujo continuo.

## 2. Rejugabilidad (partida ~10 min)
Base sana, sin manipulación:
- **Cartas** (6 en MVP): con 4 intermedios y elección de 1 de 3, hay combinatoria suficiente solo si las cartas **cambian el estilo**, no solo números. Cambios propuestos: ampliar a **10–12 cartas en Alfa**, incluyendo efectos de estilo (haz que perfora y daña en línea; luz que deja una zona iluminada 3 s; escudo de luz del faro).
- **Variación por partida:** orden/mezcla de tipos y dirección de los spawns por semilla; un «modificador de tormenta» por noche (viento que desvía el haz, niebla que reduce el alcance) como Alfa.
- **Dificultad Tormenta** (opcional) para quien domina el juego; no obligatoria.
- **Objetivos opcionales por partida** (Alfa): «No dejes pasar ningún Reptante», «Termina sin ser apagado» → cosméticos/estadísticas, nunca poder.
- **Cooperación:** cruce de haces, Foco Mayor, votación de cartas.
**Evitar:** rachas diarias, temporizadores, escasez falsa, cartas de pago ([[Monetizacion]]).

## 3. Progresión — qué es imprescindible
| Elemento | Prototipo | MVP | Después |
|---|---|---|---|
| Mejoras temporales en partida (cartas) | ❌ (solo mejoras fijas por Config) | ✅ | ampliar a 10–12 |
| Estadísticas de partida (pantalla de resultados) | ✅ mínimas | ✅ | históricas |
| Progresión de cuenta (Luz/Cristales) | ❌ | ✅ mínima | completa |
| Cosméticos y personalización | ❌ | 3–5 items | variantes laterales, mascotas |
| Desafíos/objetivos | ❌ | ❌ | Alfa |
Regla: **no se añade progresión hasta que el prototipo supere la Puerta 1** ([[MVP]]).

## 4. Multiplataforma
| Plataforma | Control propuesto | Riesgo | Mitigación |
|---|---|---|---|
| PC | Ratón apunta, clic izq. mantiene luz | Ninguno relevante | Cursor sobre el plano del suelo |
| Móvil/táctil | **Opción A (por defecto):** joystick izq. mueve; **pulgar derecho arrastra para apuntar y la luz se enciende mientras se arrastra** (un solo gesto, sin botón). **Opción B:** botón «Luz» + arrastre | Precisión baja, el pulgar tapa la pantalla, 2 pulgares ocupados | Asistencia de apuntado (snap suave a la Sombra más cercana en el cono), alcance generoso, auto-encendido ligado a apuntar |
| Mando | Stick derecho apunta, gatillo mantiene | Baja | Zona muerta |
**Evaluar A y B con un parámetro en el prototipo** (TASK-004/006) y decidir con pruebas reales. **No se da por probado nada en móvil** hasta usar dispositivos reales ([[VALIDACION-PROTOTIPO]]).

## 5. Diferenciación competitiva
**Puntos fuertes:** identidad visual clara (luz/oscuridad, legible en miniatura), partida corta, jugable solo, sin pagar por poder (diferencia ética en un mercado con gachas), cooperación con haces visibles.
**Debilidades:** género de defensa conocido; competir con un líder (*99 Nights*, ~285k CCU jun-2026, ESTIMACIÓN) en el mismo hueco; el «apuntar un cono» puede resultar superficial.
**Profundidad:** hoy es *moderada-baja* en el diseño escrito; se compensa con (a) cruce de haces, (b) enemigos con contramedidas distintas (Bruto = foco; Reptante = barrido; Gaviota = Foco Mayor), (c) cartas de estilo.
**Veredicto:** **viable para validar un prototipo**; sin problema fundamental que obligue a cambiar el concepto. La profundidad es la mayor incertidumbre y se mide en playtest ([[VALIDACION-PROTOTIPO]]).

## Cambios derivados
- Parámetro `overlapBonus` y pulsos de oleada → [[TASK-006]], [[TASK-008]].
- Control táctil A/B → [[TASK-004]].
- Registrados como decisión: [[ADR-004-validacion-concepto]].
