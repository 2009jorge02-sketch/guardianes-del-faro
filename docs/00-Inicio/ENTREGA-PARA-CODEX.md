---
tipo: entrega
actualizado: "2026-11-15 (v3: lectura progresiva, herramientas y conexiones actualizadas)"
---
# Entrega para Codex

## Resumen ejecutivo del juego
**Guardianes del Faro** (nombre y concepto **provisionales**, ver [[ADR-004-validacion-concepto]]): cooperativo 1–4 jugadores en Roblox. Una tormenta lanza Sombras de cristal contra un faro; el equipo apunta haces de luz para destruirlas durante **5 noches (~10 min)**, elige una carta de mejora entre noches y gana Luz/Cristales para cosméticos. Sin pagar por poder, sin azar de pago, apto para menores (Mild). Jugable en solitario. Detalle: [[Concepto]], [[GDD]], [[Revision-Concepto]].

## Prototipo (Fase 1) y para qué sirve
Una isla greybox generada por código, linterna con Carga, Sombras sin `Humanoid` (tope 60), Integridad, 5 noches por `Config`, HUD y resultados mínimos, herramienta de rendimiento. **Su único propósito es validar el concepto** ([[VALIDACION-PROTOTIPO]]): ¿es divertido el haz?, ¿rinde ≥30 FPS en móvil con 60 enemigos?, ¿funciona el control táctil? Hasta que se registre esa decisión **no se empieza TASK-010 ni posteriores**.

## Documentos de referencia (consultar solo la sección que cite la tarea; no leerlos todos)
[[GDD]] · [[Mecanicas]] (cifras) · [[Revision-Concepto]] · [[VALIDACION-PROTOTIPO]] · [[ARCHITECTURE]] · [[Cliente-Servidor]] · [[Seguridad]] · [[Rendimiento]] · [[Setup-Entorno]] · [[ADR-002-herramientas]] · [[ADR-003-enemigos]] · [[MVP]] · [[ROADMAP]] · [[TASKS]] · [[AGENTS]]. Índice de qué leer para cada necesidad: [[INDICE-IA]].

## Herramientas y conexiones (detalle y fuente única: [[Setup-Entorno]] y [[Estado-de-Conexiones]])
Git · Rokit 1.2.0 · Rojo 7.7.1 · StyLua 2.6.0 · Selene 0.32.0 · plugin de Rojo en Studio · **luau-lsp 1.70.1** (instalado fuera del repo; necesita definiciones de Roblox y el sourcemap de Rojo). Configs presentes: `rokit.toml`, `stylua.toml`, `selene.toml`, `.luaurc`, `.gitattributes`. **No instalado:** Luau CLI. MCP de Roblox Studio disponible (requiere Studio abierto). Ejecuta los comandos **dentro del repo**.

## Arquitectura propuesta (resumen)
`src/shared` (Config, Types, Remotes, Util) · `src/server/Services` (Match, Lighthouse, Enemy, Beam, Spotlight, Card, PlayerState, MapBuilder) · `src/client/Controllers`. Servidor autoritativo; remotes validados con rate-limit; enemigos como datos + Parts pooleadas movidas con `BulkMoveTo`.

## Primera tarea
**[[TASK-001]]** — Andamiaje Rojo (`default.project.json`, `src/`, `tests/`) y verificación del entorno. Las configs y las herramientas ya existen: solo verificar y completar.

## Orden siguiente
`TASK-002 → 003 → 004 → 005 → 012 (medir rendimiento ya) → 006 → 007 → 008 → 009`. Después: playtest y decisión (continuar / modificar / descartar). 010–011 siguen en `borrador`. Índice: [[TASKS]].

## Decisiones nuevas que debes respetar
- Controles táctiles **A** (arrastrar = apuntar y encender) y **B** (botón + arrastre) conmutables por `Config.Input.touchScheme` (TASK-004).
- `Config.Beam.overlapBonus` = 1.0 por defecto; cruce de haces listo para probar a 1.5 (TASK-006).
- Oleadas en 2–3 pulsos con respiro de 3–5 s (TASK-008).
- Plantilla de playtest y herramienta de rendimiento (TASK-012).

## Criterios globales de calidad
- `--!strict`, módulos pequeños, sin globales; `stylua --check src tests` y `selene src` limpios antes de cerrar cada tarea.
- Servidor autoritativo; todo remote validado ([[Seguridad]]).
- Valores de balance solo en `Config`, coincidentes con [[Mecanicas]].
- Sin `Humanoid` en enemigos, sin `Touched` masivo, pooling (R1).
- Cada tarea: criterios de aceptación ✔/✘ con evidencias; sin funcionalidades fuera de alcance.

## Cómo registrar resultados
Informe final en la tarea, estado `en_revision`, nota de entrega y entrada fechada en [[PROGRESS]]; mediciones y playtests en `docs/07-Registro/Pruebas/`. Detalle y puntos de control para reanudar: [[AGENTS]] y [[Flujo-Claude-Codex]]. Dudas de diseño: «Bloqueos / preguntas» de la tarea; no inventar reglas.

## Pendientes humanos
Decidir el commit del trabajo de preparación · probar Rojo↔Studio la primera vez · móvil real para validar · aprobación final del concepto tras el playtest ([[Riesgos]]).

---
## PROMPT DE INICIO PARA CODEX (copiar y pegar)

```
Eres Codex, responsable de programar el prototipo del videojuego de Roblox «Guardianes del Faro» (concepto PROVISIONAL). El diseño, la arquitectura y las tareas ya están decididos por Claude: NO rediseñes el proyecto.

Lectura inicial, progresiva (no leas nada más hasta necesitarlo):
1. AGENTS.md (reglas, entorno, estados, informe final).
2. docs/00-Inicio/INDICE-IA.md (qué documento responde a cada necesidad).
3. La tarea asignada, docs/06-Tareas/TASK-NNN.md, COMPLETA: requisitos, dependencias, criterios de aceptación, pruebas y restricciones.
4. Solo las secciones que esa tarea cita de otros documentos.
5. Las últimas líneas de docs/07-Registro/PROGRESS.md (último punto de control).

Antes de empezar comprueba que la tarea es ejecutable: estado lista y todas sus dependencias en hecha. Hoy es TASK-001: trabaja en la rama codex/task-001-scaffold, pon el estado en en_progreso, implementa solo lo que pide, ejecuta las comprobaciones indicadas y, al terminar, sigue el cierre de AGENTS.md (informe final, en_revision, entrega, PROGRESS). Después, por este orden: 002, 003, 004, 005, 012, 006, 007, 008, 009, siempre que cada una sea ejecutable. Detente tras la 009: TASK-010 y posteriores están congeladas hasta validar el prototipo.

Aplican todas las reglas de AGENTS.md (servidor autoritativo, balance solo en Config, sin instalar herramientas ni hacer push, bloqueos en la tarea, nada se marca hecha salvo por Claude). Si dejas una tarea a medias, anota el punto de control en ella.
```
