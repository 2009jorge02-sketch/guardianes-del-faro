---
tipo: entrega
tarea: T01
fecha: 2026-11-17
ejecutor: Claude Code
modelo_efectivo: claude-opus-5-5
esfuerzo_efectivo: high
estado: APPROVED_INTERNAL_V4.2
cierre: 2026-11-17, por autorrevisión según ADR-007 (no es una aprobación independiente); auditoría cruzada en el hito H1
revisor_requerido: ninguno por tarea (ADR-007); auditoría del hito H1
---
> **Cierre (2026-11-17):** T01 queda **APPROVED_INTERNAL_V4.2**. El cierre se apoya en la autorrevisión de la §Cierre del final, que resuelve una a una las observaciones de la revisión preliminar de Codex. Las secciones intermedias recogen el primer tramo y se conservan como historial.
> **2026-11-17:** [[ADR-007-revision-por-hitos]] sustituye la revisión cruzada de Codex de esta tarea. T01 se completará con autorrevisión y controles documentales; la «Solicitud de revisión» del final queda sin efecto.
# T01 · Entrega parcial (reconciliación documental y contrato de producto)

**Motivo del corte:** cuota semanal de Claude al **95 %** (queda 5 %; lectura `get_usage` a las 16:24 UTC) bajo el control V4.1. Entrega parcial guardada antes de acercarse al 2 %. **T01 no está aprobada** y no lo estará sin la revisión de Codex (`gpt-6-astra`, `high`).

## Preflight Q4
- Base: `main` @ `ed88dd0e1f641a4a0151bb522ec0da46c0a8b877`, con 10 modificados y 5 rutas sin versionar (todas conservadas).
- `backup_id`: `T01-preflight-20261117T1620Z` en `C:\Users\tatia\Documents\juego roblox1\_backups\` (fuera del repo, **mismo disco**). Contenido: `repo-all.bundle` (verificado con `git bundle verify`), `worktree.tar` (306 entradas, incluye ADR-005 y las 12 PNG; excluye `.git` y `.obsidian/plugins/*/data.json` para no duplicar tokens), `diff.patch` previo a T01, `git-status.txt`, `HEAD.txt` y `MANIFEST.sha256`.
- **No hay ensayo de restauración** (le corresponde a T02): Q4 sigue en NOT_VERIFIED.
- **Diff propio de T01** = `git diff` actual menos `diff.patch` del backup, más los archivos nuevos de abajo.

## Hecho en este tramo
| Archivo | Cambio |
|---|---|
| `docs/07-Registro/Decisiones/ADR-006-contrato-producto-v4.md` (nuevo) | D1–D14, gates Q1–Q4 con umbrales, privacidad de playtests, fechas, cuestiones abiertas, correspondencia T00–T21 ↔ TASK |
| `docs/03-Diseno/Indice-Referencias-Visuales.md` (nuevo) | 4 maestras + 8 de producción, precedencia, discrepancias impresas (no normativas) |
| `docs/03-Diseno/GDD.md` (v0.3) | Resumen, primera partida, bucle, derrota/derribo, §5.1 Q1–Q4, fuera de alcance, §9 monetización |
| `docs/03-Diseno/Mecanicas.md` | Salud, derribo y reanimación (propuesta con coste PENDIENTE); 8 arquetipos y nombres; descanso de 25 s y duración; expedición del MVP; cartas permanentes; votación y desempate de las temporales |
| `docs/03-Diseno/Monetizacion.md` | Principios nuevos (D1, D10, D5, D13); precios provisionales de cartas (D3); tabla única de cosméticos B2; tabla antigua como historial |
| `docs/03-Diseno/Progresion-Economia.md` | Recursos D2 (Luz, Monedas del Faro, Cristales de Luz); objetivos Q3/D4; aviso de que la V0.1 no cumple D4 |
| `docs/03-Diseno/Modelo-Economico.md` | Supuestos D11 (0,907 y 180 R$ base; 0,86 y 250 R$ en sensibilidad); tablas §3–4 marcadas para recalcular en T11 |
| `docs/03-Diseno/Decisiones-Monetizacion-Pendientes.md` | D1 superada por ADR-006; D2 y D3 siguen abiertas |
| `docs/05-Planificacion/MVP.md` | Prototipo sin tienda ni pagos (D13); el MVP añade derribo/reanimación y una expedición |
| `docs/00-Inicio/INDICE-IA.md` | Filas de ADR-006 y del índice visual |
| `AGENTS.md`, `CLAUDE.md` | Una línea cada uno: monetización vigente según ADR-006 |

## Verificaciones
- Wikilinks de los 11 archivos tocados: **0 rotos** (todos los destinos existen).
- Sin código de producto, sin Rojo/Studio, sin commit ni push. El original del propietario `Registro…md` no se tocó (D14).
- Ningún cambio previo se descartó: el diff anterior sigue dentro del diff actual.

## Pendiente de T01 (no hecho; siguiente tramo)
1. Textos antiguos que siguen diciendo «apagado» o «solo cosmética»: `docs/01-Vision/Pilares.md`, `docs/03-Diseno/Flujo-de-Jugabilidad.canvas`. Revisar también `Experiencia-Jugador`, `Enemigos`, `ARCHITECTURE` (PlayerStateService/derribo), UI-002, UI-003, UI-005 y UI-007, `ROADMAP` y `Riesgos`.
2. Fichas TASK: anotar en TASK-004 (Apagado → derribo) y TASK-011 (votación) que están afectadas por ADR-006, sin cambiar su estado.
3. Traducción de estados: YAML (`lista`/`en_revision`/`hecha`) ↔ contrato (`READY_FOR_REVIEW`/`APPROVED`/`CHANGES_REQUESTED`).
4. Fichas de Q1–Q4: se crean en la tarea que produzca su evidencia (ADR-006 §Gates); decidir con Codex si T01 debe crear también las plantillas.
5. `PROGRESS.md`: registrar T00 y T01.

## Q1–Q4
| Gate | Estado | Nota |
|---|---|---|
| Q1 | NOT_VERIFIED | Protocolo y privacidad mínimos en ADR-006; sin testers ni sesiones |
| Q2 | NOT_VERIFIED | Rúbrica registrada; sin activos |
| Q3 | NOT_VERIFIED | La V0.1 incumple el objetivo D4 de 12–20 h; se recalibra en T11 |
| Q4 | NOT_VERIFIED | Preflight hecho; restauración no ensayada |

## Riesgos y decisiones abiertas para el propietario
ADR-006 §Cuestiones abiertas: (1) ¿el recurso raro de reanimación son los Cristales de Luz o un recurso aparte?; (2) ¿se mantienen los cosméticos gratis por nivel o se cumple D10 al pie de la letra?; (3) ¿se renombra «Luz» (XP) para no confundirla con los Cristales de Luz?; (4) correspondencia de los 3 arquetipos iniciales. Además, el backup está en el mismo disco: no protege ante la pérdida del disco.

## Solicitud de revisión
Codex (`gpt-6-astra`, `high`): revisar este tramo contra ADR-006 y el contrato de T01 («Aceptar solo si»). Devolver `CHANGES_REQUESTED` con criterios medibles o aprobar el tramo. T01 completa necesita además los pendientes 1–5.

## Cierre (tramo 2, 2026-11-17, Claude Opus 5.5 high)
Evidencia de entrada: revisión preliminar de Codex, **CHANGES_REQUESTED — PRELIMINAR**. Sacada en modo lectura del registro de sesión local de Codex (`~/.codex/sessions/2026/11/17/rollout-…17-31-23-…jsonl`, último mensaje con T01). El texto de D15–D18 procede de las instrucciones del propietario en esas sesiones.

### Observaciones de Codex → cierre
| # | Observación | Estado | Dónde |
|---|---|---|---|
| P1-a | Correspondencia Txx↔TASK con dependencias imposibles (TASK-012 en T02; T04 frente a TASK-005; TASK-001 seleccionable; TASK-013…031; Foco Mayor) | **Cerrada** | ADR-006 §Relación (T02 solo con la infraestructura de 012; T04 no da por buena TASK-005; Foco Mayor/TASK-010 → T10); `txx` y `txx_autorizada: false` en las 12 TASK; `Tareas-Ejecutables.base` exige `txx_autorizada`; regla 6 de AGENTS; TASKS.md marcado como histórico. Los estados YAML **no cambian** |
| P1-b | «Apagado» vigente en Pilares, Experiencia, canvas, ARCHITECTURE, Cliente-Servidor, TASK-002/004/006/010, UI-002/007 | **Cerrada** | Sustituido por salud, derribo, rescate y eliminación (D5/D15); `PlayerStateChanged`; base en T05 y completo en T10; Glosario |
| P1-c | Cristales como moneda persistente (ARCHITECTURE, Seguridad, UI-004, TASK-009, canvas, ROADMAP) | **Cerrada** | Perfil `{xp, monedasFaro, cartas…}`; MatchResourceService para los Cristales de Luz de la partida; Seguridad sin doble consumo (pruebas en T10). TASKS.md «015 RewardService (Luz y Cristales)» queda como desglose histórico marcado |
| P1-d | Dos reglas de votación; descanso de 30 s; preparación 20 frente a 30 s | **Cerrada** | Mecanicas (regla única); TASK-011 (requisitos), TASK-008 (Prep 20 s ≤ 30, descanso 25 s), UI-003 (voto, tiempo, resultado, abstención), Experiencia, canvas |
| P1-e | Puerta de ADR-004 sin ubicación; umbrales distintos | **Cerrada** | ADR-006 §Puerta de validación: la produce T05 con el umbral más exigente ([[VALIDACION-PROTOTIPO]]); MVP y ROADMAP remiten a ella; distinta de Q1 |
| P2-a | D16–D18 sin propagar (Pilares, Experiencia, UI-005, Enemigos, alcance del prototipo) | **Cerrada** | Pilares, Experiencia, UI-005, Enemigos (alias históricos, RES sin renombrar), Progresión (XP y recompensas no cosméticas), Glosario; prototipo con 3 enemigos (D9/D18) en Mecanicas, MVP y Enemigos |
| P2-b | Fichas Q1–Q4 sin definir | **Cerrada** | [[PLAYTEST_PLAN]] (plan y consentimiento) y [[Protocolo-Gates-Q]] (ficha común y protocolos Q2–Q4); todo en NOT_VERIFIED |
| P2-c | Traducción de estados | **Cerrada** | [[ADR-007-revision-por-hitos]] §Estados (incluye `APPROVED_INTERNAL_V4.2`) |

### Correcciones obligatorias del propietario (1–12)
1 D15–D18 en ADR-006 y preguntas cerradas ✔ · 2 Contradicciones de Apagado, Cristales persistentes, cosméticos gratis y muerte ✔ · 3 Votación unificada ✔ · 4 Descanso de 25 s y partida de 10–15 min ✔ · 5 Rastreadora, Acechadora y Bruta ✔ · 6 Pilares, canvas, arquitectura y UI ✔ · 7 Dependencias (TASK-012 en T02) documentadas sin cambiar el orden T00–T21 ✔ · 8 TASK-004 y TASK-011 con requisitos y criterios nuevos ✔ · 9 Equivalencia de estados ✔ · 10 Plantillas Q1–Q4, en NOT_VERIFIED ✔ · 11 Las 12 referencias se mantienen ([[Indice-Referencias-Visuales]]) ✔ · 12 V0.1 como hipótesis; las 41–58 h van a T11 ✔

### Comprobaciones (salidas reales)
- Enlaces: script local sobre 118 archivos (`docs/**/*.md`, `*.canvas`, AGENTS, CLAUDE; sin `_plantillas`) → **0 rotos**.
- YAML de las 12 TASK: `estado`, `depende_de`, `txx` y `txx_autorizada` presentes y sin claves duplicadas → OK; estados intactos (10 `lista`, 2 `borrador`).
- Sustituciones: 56 + 24 + 6, cada una comprobada antes de escribir (texto encontrado el número exacto de veces) → **0 fallos**.
- Búsqueda de reglas antiguas (`apagad`, empate aleatorio, intermedio de 30 s, «Luz y Cristales», «cosméticos por nivel», «solo cosm», `PlayerStunned`, `stun(`): solo quedan menciones marcadas como historial, `Revision-Concepto.md` (revisión fechada, histórica), el desglose histórico de TASKS.md y usos legítimos (linterna o faroles «apagados»).
- Conservación: las 16 rutas del preflight siguen presentes. De las 77 líneas añadidas antes de T01, 23 se cambiaron **a propósito** (reglas antiguas sustituidas, versiones y fechas de cabecera); su contenido sigue en el backup `diff.patch` y, donde aplica, como «Historial» en los documentos.
- **Límites:** sin tests de código (T01 no tiene código); validación de Obsidian por script, no en la aplicación; Q1–Q4 en NOT_VERIFIED.

### Riesgos y bloqueos restantes
- Coste de reanimación y autorreanimación, Cristales de Luz iniciales y sus fuentes: pendientes; bloquean implementar D15 (T10), no diseñarlo.
- El backup está en el mismo disco y sin ensayo de restauración (lo hace T02).
- No hay commit: el trabajo de ADR-005 y de T00/T01 solo existe en local y en el backup.
- Los cortes de hito H1–H4 los definió Claude por encargo del propietario; conviene que los confirme.
- Pequeño residuo histórico sin tocar: `Revision-Concepto.md:37` habla de «ser apagado» (revisión fechada).
