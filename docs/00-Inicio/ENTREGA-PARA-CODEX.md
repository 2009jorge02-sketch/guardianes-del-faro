---
tipo: entrega
actualizado: "2026-11-14 (v2: herramientas instaladas, concepto provisional, validación)"
---
# Entrega para Codex

## Resumen ejecutivo del juego
**Guardianes del Faro** (nombre y concepto **provisionales**, ver [[ADR-004-validacion-concepto]]): cooperativo 1–4 jugadores en Roblox. Una tormenta lanza Sombras de cristal contra un faro; el equipo apunta haces de luz para destruirlas durante **5 noches (~10 min)**, elige una carta de mejora entre noches y gana Luz/Cristales para cosméticos. Sin pagar por poder, sin azar de pago, apto para menores (Mild). Jugable en solitario. Detalle: [[Concepto]], [[GDD]], [[Revision-Concepto]].

## Prototipo (Fase 1) y para qué sirve
Una isla greybox generada por código, linterna con Carga, Sombras sin `Humanoid` (tope 60), Integridad, 5 noches por `Config`, HUD y resultados mínimos, herramienta de rendimiento. **Su único propósito es validar el concepto** ([[VALIDACION-PROTOTIPO]]): ¿es divertido el haz?, ¿rinde ≥30 FPS en móvil con 60 enemigos?, ¿funciona el control táctil? Hasta que se registre esa decisión **no se empieza TASK-010 ni posteriores**.

## Documentos fundamentales
[[GDD]] · [[Mecanicas]] (cifras) · [[Revision-Concepto]] · [[VALIDACION-PROTOTIPO]] · [[ARCHITECTURE]] · [[Cliente-Servidor]] · [[Seguridad]] · [[Rendimiento]] · [[Setup-Entorno]] · [[ADR-002-herramientas]] · [[ADR-003-enemigos]] · [[MVP]] · [[ROADMAP]] · [[TASKS]] · [[AGENTS]]

## Herramientas (ya instaladas y verificadas el 2026-11-14)
Git 2.56.1 · Rokit 1.2.0 · Rojo 7.7.1 · StyLua 2.6.0 · Selene 0.32.0 · plugin de Rojo copiado a Studio. Configs ya presentes: `rokit.toml`, `stylua.toml`, `selene.toml`, `.luaurc`, `.gitattributes`. **No instalados:** Luau CLI y luau-lsp (no los instales sin autorización). Roblox Studio está instalado; la conexión Rojo↔Studio la confirma el usuario manualmente la primera vez ([[Setup-Entorno]]). Ejecuta los comandos **dentro del repo**.

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
1. En la tarea: «Informe final» ([[AGENTS]]) y estado `en_revision`.
2. Entrada fechada en [[PROGRESS]].
3. Mediciones y playtests en `docs/07-Registro/Revisiones/`.
4. Dudas de diseño: «Bloqueos / preguntas» de la tarea; no inventar reglas.

## Pendientes humanos
Remoto de GitHub y primer commit · probar Rojo↔Studio · móvil real para validar · aprobación final del concepto tras el playtest ([[Riesgos]]).

---
## PROMPT DE INICIO PARA CODEX (copiar y pegar)

```
Eres Codex, el responsable de programar el prototipo del videojuego de Roblox «Guardianes del Faro» (concepto PROVISIONAL, pendiente de validar). El diseño, la arquitectura y las tareas ya están decididos por Claude: NO rediseñes el proyecto.

Antes de escribir código, en este repositorio:
1. Lee completo AGENTS.md (reglas, entorno verificado, ciclo de estados, informe final).
2. Lee docs/00-Inicio/ENTREGA-PARA-CODEX.md y docs/07-Registro/PROGRESS.md.
3. Lee docs/03-Diseno/GDD.md, docs/03-Diseno/Mecanicas.md (única fuente de cifras), docs/03-Diseno/Revision-Concepto.md, docs/05-Planificacion/VALIDACION-PROTOTIPO.md, docs/04-Arquitectura/ARCHITECTURE.md, Cliente-Servidor.md, Seguridad.md, Rendimiento.md y Setup-Entorno.md, y los ADR de docs/07-Registro/Decisiones/.
4. Lee docs/05-Planificacion/TASKS.md y las tareas docs/06-Tareas/TASK-001.md a TASK-012.md.

Entorno (ya instalado; ejecuta los comandos dentro del repo): Git, Rokit, Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0 y el plugin de Rojo. Si una terminal no ve git/rokit, refresca el PATH (ver Setup-Entorno.md). No instales Luau CLI, luau-lsp ni nada más sin avisar al usuario. No hagas push ni crees remotos.

Comienza con TASK-001 en la rama codex/task-001-scaffold: cambia su estado a en_progreso, implementa solo lo que pide, ejecuta las comprobaciones indicadas, y al terminar rellena su «Informe final», pon el estado en en_revision y añade una entrada en PROGRESS.md. Después sigue este orden: 002, 003, 004, 005, 012, 006, 007, 008, 009. Detente tras la 009: no empieces TASK-010 ni posteriores (están congeladas hasta validar el prototipo).

Reglas clave: servidor autoritativo y todo remote validado; valores de balance solo en Config y coincidentes con Mecanicas.md; stylua --check src tests y selene src limpios; si falta una decisión de diseño, anótala en «Bloqueos / preguntas» y no inventes reglas; no añadas funcionalidades fuera de alcance; no marques ninguna tarea como hecha (lo hace Claude tras revisar evidencias).
```
