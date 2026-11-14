---
tipo: planificacion
actualizado: 2026-11-14
---
# Riesgos y decisiones pendientes

| ID | Riesgo | Prob. | Impacto | Mitigación | Estado |
|---|---|---|---|---|---|
| R1 | Rendimiento móvil con 60 enemigos y luz | Media | Alto | Sin Humanoid, pooling, [[TASK-012]] temprano, fallback [[ADR-003-enemigos]] | Abierto |
| R2 | El haz no resulta divertido | Media | Alto | Prototipo mínimo y playtest antes de invertir en contenido; asistencia de apuntado | Abierto |
| R3 | Sin retención suficiente sin pagos/azar | Media | Alto | Cartas, variantes, Tormenta, cosméticos; medir D1/D7 en Beta | Abierto |
| R4 | Mercado saturado / líder (*99 Nights*) | Alta | Medio | Diferenciar por partida corta, luz y cooperación flexible; no competir en tamaño | Abierto |
| R5 | Codex itera red/servidor sin depuración en vivo | Media | Medio | Tareas pequeñas, pruebas guiadas, logs claros, [[TASK-012]] | Abierto |
| R6 | Mala monetización/ética con menores | Baja | Alto | Principios de [[Monetizacion]]; revisión de políticas | Mitigado en diseño |
| R7 | Datos de mercado no verificados | Alta | Medio | Marcados [PV]; contrastar en roblox.com/charts y Creator Hub antes de Alfa | Abierto |
| R8 | Audio/arte sin licencia clara | Media | Medio | Usar solo recursos con licencia verificada | Abierto |
| R9 | Git no disponible en el PATH | Alta | Medio | Git 2.56.1 ya instalado; terminales antiguas necesitan refrescar PATH ([[Setup-Entorno]]) | Resuelto |
| R10 | Profundidad insuficiente del apuntado de luz | Media | Alto | Cruce de haces, enemigos con contramedidas, cartas de estilo; [[VALIDACION-PROTOTIPO]] | Abierto |
| R11 | Control táctil insuficiente | Media | Alto | Esquemas A/B y prueba en móvil real | Abierto |

## Decisiones pendientes del usuario
1. Aprobar el concepto [[ADR-001-concepto]] (nombre provisional).
2. Autorizar instalación de Git, Rokit/Rojo/StyLua/Selene y el plugin de Rojo ([[ADR-002-herramientas]]).
3. Crear remoto en GitHub y decidir visibilidad.
4. Decidir política de audio/arte (propio, IA, biblioteca).
5. Máximo de jugadores por servidor (propuesto 4).
