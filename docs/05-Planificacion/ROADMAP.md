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
- **Fin:** criterios de [[MVP]] §Puerta 1: ≥30 FPS móvil con 60 enemigos, y ≥3 testers (no el autor) completan una noche y quieren repetir.
- **Pruebas:** manuales en Studio (1 y 4 clientes), overlay de rendimiento, unitarias de cálculo.

## Fase 2 · MVP
- **Objetivo:** partida completa de principio a fin con progreso persistente.
- **Entregables:** Foco Mayor, cartas, Reptante y Bruto, persistencia, recompensas (Luz/Cristales), menú, personalización mínima, tutorial en acción, ajustes básicos.
- **Dependencias:** Puerta 1.
- **Riesgos:** R3 retención sin pagos; persistencia.
- **Fin:** Puerta 2 en [[MVP]]: partida completa estable, guardado verificado (reintentos), sin errores críticos en 20 partidas seguidas.

## Fase 3 · Alfa
- **Objetivo:** ampliar mecánicas y sistemas.
- **Entregables:** Gaviotas y jefe, dificultades Tormenta, tienda cosmética y compras, variantes de linterna, arte/audio reales integrados, accesibilidad completa.
- **Fin:** contenido completo del GDD v1; sin exploits conocidos en remotes.

## Fase 4 · Beta
- **Objetivo:** rendimiento, errores y jugadores reales.
- **Entregables:** analítica propia, pruebas con jugadores (acceso restringido), equilibrio, optimización móvil, revisión de políticas.
- **Fin:** abandono en primera partida y D1/D7 medidos; plan de ajuste.

## Fase 5 · Lanzamiento
- **Entregables:** página de la experiencia, iconos/miniaturas, cuestionario de madurez, soporte de errores, plan de actualizaciones.
- **Fin:** publicación y primer ciclo de mejoras tras datos reales.

## Actualizaciones posteriores (ideas, no compromisos)
Nuevo mapa «Arrecife», eventos estacionales con cosméticos recuperables, nuevo jefe, modo diario sin presión, modo cooperativo infinito.
