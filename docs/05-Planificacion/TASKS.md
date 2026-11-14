---
tipo: planificacion
actualizado: 2026-11-14
---
# Tareas

Vista dinámica: abrir [[Tareas.base]] (Bases de Obsidian, filtra `docs/06-Tareas`). Ciclo y estados: [[AGENTS]]. Fases: [[ROADMAP]].

## Orden de ejecución recomendado (Fase 1)
`001 → 002 → 003 → 004 → 005 → 012 (medir rendimiento pronto) → 006 → 007 → 008 → 009`
Puerta 1 de [[MVP]]. Luego Fase 2: 010, 011 y las siguientes.

| ID | Tarea | Fase | Dep. | Estado |
|---|---|---|---|---|
| [[TASK-001]] | Andamiaje Rojo y herramientas | 1 | — | lista |
| [[TASK-002]] | Config, Types, Remotes, utilidades | 1 | 001 | lista |
| [[TASK-003]] | MapBuilder: isla y faro | 1 | 002 | lista |
| [[TASK-004]] | Jugador, entrada y cámara | 1 | 002, 003 | lista |
| [[TASK-005]] | EnemyService y Sombra | 1 | 002, 003 | lista |
| [[TASK-012]] | Rendimiento y playtest | 1 | 005 | lista |
| [[TASK-006]] | Linterna (BeamService + visual) | 1 | 004, 005 | lista |
| [[TASK-007]] | Integridad del Faro | 1 | 005 | lista |
| [[TASK-008]] | MatchService (5 noches) | 1 | 005, 007 | lista |
| [[TASK-009]] | HUD y resultados | 1 | 006, 008 | lista |
| [[TASK-010]] | Foco Mayor | 2 | 006, 008, 009 | borrador |
| [[TASK-011]] | Cartas de mejora | 2 | 008, 009 | borrador |

## Tareas futuras (esquema; se detallarán al cerrar la fase anterior)
**Fase 2 · MVP:** 013 Reptante y Bruto · 014 DataService (persistencia) · 015 RewardService (Luz y Cristales) · 016 Menú principal y personalización · 017 Tutorial en acción y ajustes (accesibilidad) · 018 Pruebas de 20 partidas seguidas.
**Fase 3 · Alfa:** 019 Gaviotas y jefe Marea Negra · 020 Dificultades Tormenta · 021 Tienda cosmética y compras (ProcessReceipt) · 022 Variantes de linterna · 023 Integración de arte final · 024 Audio · 025 Revisión de seguridad de remotes.
**Fase 4 · Beta:** 026 Analítica propia (abandono 1.ª partida, D1/D7) · 027 Optimización móvil · 028 Correcciones de playtest · 029 Revisión de políticas Roblox.
**Fase 5 · Lanzamiento:** 030 Página de experiencia, iconos y cuestionario de madurez · 031 Soporte y plan de actualizaciones.

**Congelado:** desde TASK-010 en adelante nada empieza hasta ejecutar [[VALIDACION-PROTOTIPO]] y registrar la decisión ([[ADR-004-validacion-concepto]]). Cambios añadidos tras [[Revision-Concepto]]: esquemas táctiles A/B (TASK-004), `overlapBonus` (TASK-006), pulsos de oleada (TASK-008), plantilla de playtest (TASK-012), y TASK-001 reducida porque las herramientas y configs ya están instaladas ([[Setup-Entorno]]).

Regla: una tarea pasa a `hecha` solo tras revisión de Claude con evidencias ([[CLAUDE]]).

## Relacionado (añadido en la mejora del vault)
- Panel de supervisión: [[Centro-de-Control]] · Resumen vivo del estado: la verdad está en el YAML de cada tarea ([[Tareas.base]]); esta tabla es solo un resumen histórico.

- Aviso: «lista» en esta tabla significa **documentada**; ejecutable es solo la que tiene todas sus dependencias `hecha` (ver [[Tareas-Ejecutables.base]]).
