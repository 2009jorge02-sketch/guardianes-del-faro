---
tipo: revision
tema: Revisión estratégica de los 3 finalistas
fecha: 2026-11-14
revisor: subagente general-purpose con model=opus, effort=medium (equivalente a strategic-reviewer; el agente registrado no estaba cargado)
resultado: elegir Guardianes del Faro modificado
---
# Revisión estratégica de finalistas

Entrada: [[Ideas-Evaluadas]]. Decisión resultante: [[ADR-001-concepto]].

## Críticas de método (aceptadas)
- Viabilidad (15 %) + Riesgo (5 %) pesan poco para un equipo de una persona que programa vía Codex sin depurar en vivo. **Sensibilidad recalculada por mí** (Atraer 15, Reten. 20, Difer. 15, Viab. 25, Monet. 15, Ampl. 0, Riesgo 10): Horda **7,30**, Faro **7,15**, Último Tren **6,50**. Faro y Horda quedan empatados en la práctica; Último Tren cae.
- Las diferencias de 0,05–0,30 entre finalistas son ruido; retención y monetización iguales (8 y 7) no tienen base en datos.
- La tesis «hueco de supervivencia coop» se apoya en un único caso (*99 Nights*) → puede significar líder ya asentado.
- Competidores directos sin analizar (p. ej. *Dead Rails*, tren en páramo hostil): **[pendiente de verificación]**; si es cierto, la diferenciación de Último Tren estaba inflada.

## Por finalista
| Concepto | Veredicto | Motivo principal |
|---|---|---|
| Guardianes del Faro | Elegir, **modificado** | Mejor gancho visual; complejidad real media-alta si lleva exploración, inventario y rol único |
| Horda de Cristal | Base técnica | Primer minuto fuerte, datos-dirigido; pero enemigos masivos con `Humanoid` no escalan y gancho débil |
| Último Tren | Descartar | Jugadores sobre base móvil = problemas de *network ownership*; peor para iterar a ciegas con Codex |
| Cuerda y Cumbre (reserva) | Descartar | `RopeConstraint` entre clientes → rubber-banding; subgénero clonado |
| Pastelería Fantasma (reserva) | Reserva viable | Sincronización sensible a latencia |

## Modificaciones al concepto (adoptadas)
1. Defensa por oleadas de un **objetivo fijo** (el faro), **sin fase de día ni inventario** en MVP; solo intermedio de 30 s para elegir mejora.
2. El haz **no depende de una sola persona**: linterna individual + Foco Mayor compartido con modo automático → **jugable en solitario**.
3. Enemigos **sin `Humanoid`**, tope estricto desde el inicio.
4. Meta-progresión **cosmética/lateral**; sin pagar por poder, revivir ni azar de pago.
5. Partida **8–10 min** (no 15); clasificación **Mild**.

## Tres incertidumbres a validar en el prototipo
1. ¿Es divertido el haz en los primeros 60 s, solo o con desconocidos? (abandono en 1.ª partida)
2. ¿Rinde en móvil de gama baja con enemigos y luz nocturna a ≥30 FPS? Si falla, el concepto cambia.
3. ¿Hay motivo para volver en D1 sin pagos? ¿Puede Codex iterar la red/servidor sin depuración en vivo?

## No verificado por el revisor
CCU de terceros, estado de *Dead Rails*/wave survivors en Roblox, límites móviles, retención por género, compatibilidad Codex–MCP de Studio.
