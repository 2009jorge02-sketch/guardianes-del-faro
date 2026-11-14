---
id: TASK-012
titulo: Herramientas de rendimiento y playtest (overlay y comandos de depuración)
estado: lista
prioridad: alta
fase: 1
depende_de: [TASK-005]
responsable: Codex
creado: 2026-11-14
tipo: tarea-codex
fecha_actualizacion: 2026-11-14
---
# TASK-012 · Rendimiento y playtest

## Objetivo
Medir pronto el riesgo R1: FPS, ping y carga con 50/100/200 enemigos, y registrar resultados reproducibles.

## Contexto
[[Rendimiento]], [[ADR-003-enemigos]], [[Riesgos]] (R1). Se ejecuta **justo después de TASK-005** para validar el riesgo antes de construir más.

## Requisitos
1. **Cliente:** `DebugOverlay` (activable con F9 o botón en Studio) que muestra FPS, ping, nº de enemigos (atributo replicado) y memoria aproximada.
2. **Servidor:** `DebugService` activo **solo si `RunService:IsStudio()`**; comandos: `debugSpawn(n)`, `debugClear()`, `debugSetCap(n)` (solo para pruebas).
3. Script que genere automáticamente un bloque de **informe en Markdown** con N, FPS medio/mín, ping y tiempo de `step`, para pegar en `docs/07-Registro/Revisiones/perf-YYYY-MM-DD.md`.
4. Procedimiento documentado (`docs/04-Arquitectura/Pruebas-Rendimiento.md`) para ejecutar la prueba en: PC, emulador móvil de Studio y **dispositivo móvil real** (a cargo del usuario).

5. Plantilla de **registro de playtest** en `docs/07-Registro/Revisiones/playtest-plantilla.md` con los campos de [[VALIDACION-PROTOTIPO]] (dispositivo, FPS, comprensión <30 s, primera destrucción, nº de partidas voluntarias, comodidad táctil A/B 1–5, comentarios literales). Es solo la plantilla; no se inventan resultados.

## Componentes afectados (propuesta)
`src/client/Controllers/DebugOverlay.luau`, `src/server/Services/DebugService.luau`, `docs/04-Arquitectura/Pruebas-Rendimiento.md`.

## Criterios de aceptación
- [ ] Overlay visible con valores que cambian al spawnear enemigos.
- [ ] Los comandos no existen en servidores de producción (comprobado con `IsStudio`).
- [ ] Existe el informe con resultados para 50, 100 y 200 enemigos en PC y emulador.
- [ ] El documento de procedimiento permite al usuario repetirlo en móvil.
- [ ] **Veredicto explícito** en el informe: ¿se cumple 30 FPS móvil con 60 enemigos? Si no, recomendación (bajar tope o activar opción B de [[ADR-003-enemigos]]).

## Pruebas
Ejecutar las 3 configuraciones indicadas y adjuntar el informe.

## Restricciones
Nada de depuración activa en producción; sin dependencias externas.

## Entregable
Rama `codex/task-012-perf` + informe de rendimiento.

## Informe final
(Formato de [[AGENTS]].)

## Bloqueos / preguntas
—
