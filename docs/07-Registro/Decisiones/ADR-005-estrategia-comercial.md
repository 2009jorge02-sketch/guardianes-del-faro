---
id: ADR-005
titulo: Estrategia comercial y objetivo económico
estado: aceptada
fecha: 2026-11-16
decide: usuario (aprobación con condiciones) + Claude (propuesta)
---
# ADR-005 · Estrategia comercial

## Contexto
El proyecto añade un segundo objetivo: ingresos reales y sostenibles que financien las herramientas y proyectos de IA del usuario. Análisis: [[Modelo-Economico]] (cifras y fórmulas), [[Adquisicion-Organica]], [[Decisiones-Monetizacion-Pendientes]]. Concepto base: [[ADR-001-concepto]] y [[ADR-004-validacion-concepto]].

## Decisiones definitivas
1. **Se mantiene Guardianes del Faro** como concepto principal (sigue sujeto a [[VALIDACION-PROTOTIPO]]; no se cambia de juego por ahora).
2. **Objetivo comercial oficial:** 100–300 €/mes de ingresos **canjeables (DevEx) antes de impuestos**, con potencial de superarlos. Es una meta, no una previsión. El éxito no se mide por visitas ([[Modelo-Economico]] §6).
3. **Aprobado:** reforzar la progresión; escalera de precios cosméticos; mejorar la visibilidad de los productos; analítica comercial desde etapas tempranas; preparar monetización recurrente para fases posteriores.
4. **Aprobado:** estrategia de adquisición orgánica sin presupuesto inicial ([[Adquisicion-Organica]]); no se asume tráfico algorítmico por sí solo.
5. **NO aprobado todavía (decisiones abiertas, en [[Decisiones-Monetizacion-Pendientes]]):** vender Cristales, aceleradores de progresión, activar suscripciones. Hasta decidir, los Cristales se ganan solo jugando y no hay suscripción ni aceleradores.
6. Sin ampliar el alcance del MVP: la analítica comercial es mínima (eventos de embudo) y [[TASK-001]] sigue siendo una tarea técnica independiente.
7. **Git (resuelto):** Claude y Obsidian trabajan en la raíz sobre `main`; Codex usa un worktree fuera del vault y puede hacer commits locales en su rama cuando se autorice su tarea. Sin push ni merge sin aprobación expresa del usuario.
8. Consumo de Claude Pro: reutilizar la investigación documentada; sin subagentes ni búsquedas repetidas salvo datos críticos sin resolver; modelo y esfuerzo mínimos suficientes.

## Consecuencias
Se actualizan [[GDD]], [[Monetizacion]], [[Progresion-Economia]], [[ROADMAP]], [[MVP]] y [[Riesgos]]. Fase 2 (TASK-010 en adelante) sigue congelada según ADR-004. Ninguna tarea nueva se crea todavía (propuesta de analítica en [[ROADMAP]]).

## Riesgos
Todas las cifras económicas son hipótesis hasta tener datos del Beta. Datos oficiales leídos con herramientas de resumen: releer los críticos antes del primer canje.
