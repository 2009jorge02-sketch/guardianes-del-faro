---
tipo: planificacion
actualizado: 2026-11-14
---
# Roadmap

Sin fechas: los plazos dependen de la disponibilidad de Codex y de los resultados de playtest. Cada fase termina con una **puerta de calidad** (si no se cumple, no se avanza). Tareas: [[TASKS]]. Alcance MVP: [[MVP]]. Riesgos: [[Riesgos]].

## Fase 1 · Prototipo jugable
- **Objetivo:** demostrar que el haz de luz es divertido y que 60 enemigos rinden en móvil.
- **Entregables:** isla greybox, linterna, Sombras, Faro con Integridad, 5 noches por Config, HUD y resultados mínimos, herramienta de rendimiento. Tareas 001–009 y 012.
- **Requisitos:** Git, Rojo/StyLua/Selene aprobados ([[ADR-002-herramientas]]).
- **Dependencias:** ninguna externa.
- **Riesgos:** R1 rendimiento, R2 diversión.
- **Fin:** criterios de [[MVP]] §Puerta 1 y de la puerta de validación de [[ADR-006-contrato-producto-v4]] (≥30 FPS en móvil con 60 enemigos; ≥5 externos según [[VALIDACION-PROTOTIPO]]).
- **Pruebas:** manuales en Studio (1 y 4 clientes), overlay de rendimiento, unitarias de cálculo.

## Fase 2 · MVP
- **Objetivo:** partida completa de principio a fin con progreso persistente.
- **Entregables:** Foco Mayor, cartas, salud/derribo/reanimación y expedición, persistencia, recompensas (XP/Monedas del Faro), menú, personalización mínima, tutorial en acción, ajustes básicos y **analítica comercial mínima** (embudo: entra, completa noche 1, repite, abre tienda; propuesta de tarea, aún no creada; sin ampliar el alcance jugable).
- **Dependencias:** Puerta 1.
- **Riesgos:** R3 retención sin pagos; persistencia.
- **Fin:** Puerta 2 en [[MVP]]: partida completa estable, guardado verificado (reintentos), sin errores críticos en 20 partidas seguidas.

## Fase 3 · Alfa
- **Objetivo:** ampliar mecánicas y sistemas.
- **Entregables:** Gaviotas y jefe, dificultades Tormenta, tienda cosmética y compras (escalera de precios en Robux directos; sin vender Cristales), variantes de linterna, arte/audio reales integrados, accesibilidad completa.
- **Fin:** contenido completo del GDD v1; sin exploits conocidos en remotes.

## Fase 4 · Beta
- **Objetivo:** rendimiento, errores y jugadores reales.
- **Entregables:** analítica propia (D1/D7 frente al benchmark de Creator Hub, conversión, gasto por comprador), pruebas con jugadores (acceso restringido), pruebas de icono y miniatura, equilibrio, optimización móvil, revisión de políticas.
- **Fin:** abandono en primera partida y D1/D7 medidos; plan de ajuste; **puerta comercial** evaluada (abajo).

## Fase 5 · Lanzamiento
- **Entregables:** página de la experiencia, iconos/miniaturas, cuestionario de madurez, soporte de errores, plan de actualizaciones y plan de adquisición orgánica ejecutado ([[Adquisicion-Organica]]).
- **Fin:** publicación y primer ciclo de mejoras tras datos reales.

## Puerta comercial (tras el Beta)
Solo se amplía la monetización (decisiones D1–D3 de [[Decisiones-Monetizacion-Pendientes]]) si, con jugadores reales: D1 ≥ mediana del benchmark propio, comprador ≥ 1 % y gasto por comprador ≥ 250 Robux/mes, y la adquisición aporta jugadores a un coste de tiempo asumible. Umbrales de [[Modelo-Economico]] §7 (hipótesis; se recalibran). Si no se cumple: modificar progresión o productos antes de añadir contenido.

## Actualizaciones posteriores (ideas, no compromisos)
Nuevo mapa «Arrecife», eventos estacionales con cosméticos recuperables, nuevo jefe, modo diario sin presión, modo cooperativo infinito; suscripción solo si se aprueba D3.
