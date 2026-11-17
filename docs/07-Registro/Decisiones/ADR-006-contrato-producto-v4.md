---
id: ADR-006
titulo: Contrato de producto V4.1 — cartas, recursos, derribo y gates de calidad
estado: aceptada
fecha: 2026-11-17
decide: usuario (D1–D14, autorización del 2026-11-17) + Claude (redacción T01)
sustituye: principio «solo cosmética» de [[Monetizacion]] §Principios 1–2 y el uso de Cristales de [[ADR-005-estrategia-comercial]] §5
tarea: T01
---
# ADR-006 · Contrato de producto V4.1

## Contexto
La auditoría T00 (aprobada en [[REV-T00-2026-11-17]]) y el paquete V4.1 (Registro de Ideas, Economía/Procedural/3D, Guía Visual, Investigación Comercial, Plan maestro de 22 tareas) contradicen varias reglas del repo. El 2026-11-17 el propietario resolvió D1–D14. Este ADR las registra; los documentos de diseño las aplican y enlazan aquí. **No se borra el historial:** [[ADR-004-validacion-concepto]] y [[ADR-005-estrategia-comercial]] siguen vigentes salvo en lo que este ADR sustituye expresamente.

## Decisiones
| ID | Decisión |
|---|---|
| D1 | **Cartas permanentes:** se desbloquean con Monedas del Faro **o** con Robux. Funcionalidad idéntica por ambas vías. Prohibido: ventajas de pago imposibles de conseguir gratis, monetización agresiva, incentivos artificiales de pago. **Sustituye** el principio «solo cosmética» de [[Monetizacion]]. |
| D2 | **Dos recursos distintos:** *Cristales de Luz* = recurso estratégico **dentro de una partida** (no persiste). *Monedas del Faro* = moneda permanente de progresión, se gana jugando. El tope heredado de 80 Cristales por partida **no** se aplica a las Monedas del Faro. |
| D3 | Precios por rareza 6 000–140 000 Monedas / 29–299 R$ ([[Modelo-Economico]] §Hipótesis V0.1): **solo valores provisionales para simulación**, no precios. |
| D4 | **Legendarias:** objetivo de diseño ≈ **12–20 h** de juego gratuito para la primera legendaria en un perfil habitual; se resuelve en T11 con el simulador Q3. Cualquier barrera > 20 h exige justificación y nueva aprobación (la alerta Q3 del contrato salta a > 40 h con 50 % de victorias). |
| D5 | **Salud, derribo, rescate y eliminación.** La estación de reanimación consume un **recurso raro compartido** que compite con la defensa del faro. En solitario: autorreanimación limitada si hay recurso; si no, derrota. **Prohibido vender reanimaciones** o ese recurso por Robux. El coste exacto se documenta en [[Mecanicas]] antes de implementarlo. |
| D6 | **MVP con una expedición exterior completa** (riesgo, recompensa, enemigos que persiguen). La variedad procedural se aplaza hasta validar ese bucle. |
| D7 | **Cartas temporales = mejoras de equipo**, elegidas por **votación** entre 3 opciones tras superar las noches 1–4. En solitario decide el jugador. Desempate reproducible en [[Mecanicas]] §Cartas temporales. |
| D8 | Partidas de **10–15 min**, 5 noches, **descansos de 25 s** (ajustables 20–30 s tras pruebas). |
| D9 | **Una especie: la Sombra**, con 8 arquetipos de diseño. Prototipo con 3, que reutilizan los nombres históricos ([[Mecanicas]] §Enemigos). |
| D10 | **Cosméticos solo por Robux.** Única tabla provisional: rangos de Economía V4.1 §B2 ([[Monetizacion]]). Las demás tablas quedan como historial. |
| D11 | Modelo económico base: **0,907 €/USD y 180 R$ por comprador**; sensibilidad con 0,86 €/USD y 250 R$. Tipos de cambio, DevEx y condiciones de Roblox se actualizan y citan al usarlos. Ninguna cifra hipotética se presenta como ingreso. |
| D12 | Las recomendaciones de monetización «solo cosmética» de la Investigación Comercial quedan como **contexto histórico**, sustituidas por D1. El resto de esa investigación (mercado, Share Links, puertas A–E) sigue siendo válido. |
| D13 | **ADR-004 sigue vigente:** el prototipo se valida sin tienda real, sin pagos y sin persistencia comercial. La monetización se diseña ya, pero se implementa en las fases previstas, después de validar el prototipo. |
| D14 | Nombre canónico del plan maestro: **`01_PLAN_MAESTRO_22_TAREAS.md`** (verificado en `Downloads`, SHA256 `662B683D…`). La cita `01_PLAN_MAESTRO_TAREAS_Y_MODELOS.md` del Registro V4.1 §12 es una errata. El original del propietario **no se edita**, para no romper su huella SHA256. |
| D15 | **Reanimación con Cristales de Luz**, no con un recurso aparte. Rescatar a un derribado **no** consume cristales; reanimar a un eliminado **sí** consume Cristales de Luz compartidos, que compiten con la defensa del faro. En solitario: autorreanimación limitada con coste. Precio exacto pendiente de balanceo. |
| D16 | **Cosméticos desbloqueables solo por Robux.** Las recompensas de nivel que daban cosméticos se sustituyen por Monedas del Faro, progresión de cartas o recompensas jugables gratuitas. Los aspectos y el equipamiento **básicos** siguen siendo gratuitos. |
| D17 | La XP pasa a llamarse **Experiencia de Guardián (XP)**, distinta de los Cristales de Luz (recurso de partida) y de las Monedas del Faro (progresión permanente). |
| D18 | **Enemigos del prototipo confirmados:** Rastreadora (antes Sombra, básica), Acechadora (antes Reptante, rápida) y Bruta (antes Bruto, resistente), todas variantes de la Sombra. Se conserva la trazabilidad de los nombres históricos. |

## Gates de calidad Q1–Q4 (contrato V4.1, umbrales iniciales)
Estado actual de los cuatro: **NOT_VERIFIED**. Se verifican en sus tareas, nunca por declaración.
- **Q1 · Personas reales:** ≥ 5 personas externas a los agentes, ≥ 1 sesión en móvil y ≥ 1 multijugador; cero P0/P1 abiertos; ≥ 4/5 volverían a jugar, entienden el objetivo tras el tutorial y completan el onboarding sin ayuda. Lo coordina T19 y lo valida T20. Si faltan testers: `WAITING_OWNER: HUMAN_PLAYTEST`. Privacidad mínima: §Privacidad de playtests.
- **Q2 · Arte en Roblox:** rúbrica de 100 puntos (silueta 25, modelado/materiales 20, iluminación/paleta 15, animación/telegraphing 25, VFX/legibilidad 15). Primer enemigo, familias críticas y jefes: ≥ 85/100 y ≥ 70 % en cada dimensión, con `.blend`, export, capturas y vídeo en Studio. El rendimiento es un gate aparte. Se fija en T03 y se aplica en T04/T16/T20.
- **Q3 · Economía:** simulador reproducible en T11 con estos escenarios: victorias 30/50/70 %, conversión 1/3/5 %, gasto 50/180/350 R$, 5 rarezas y objetivos de 100/200/300/1 000 €. La primera común debe conseguirse en ≤ 10 partidas; la legendaria, en 12–20 h (D4).
- **Q4 · Recuperación:** preflight antes de cada tarea con cambios y ensayo de restauración aislado en T02; se repite antes de T04/T07/T09/T12/T16/T19/T21. Un commit solo no es copia de seguridad de lo no versionado.
- Rutas de evidencia acordadas, dentro del vault: `docs/qa/PLAYTEST_PLAN.md` (creado en T01: plan y consentimiento), `docs/qa/PLAYTEST_RESULTS_ANON.md`, `docs/qa/VISUAL_SCORECARD.md`, `docs/qa/ECONOMY_SIMULATION.md`, `docs/qa/RESTORE_DRILL.md` y `docs/qa/ASSET_MANIFEST.md`. Las fichas de evidencia se crean, a partir de las plantillas de [[Protocolo-Gates-Q]], en la tarea que produce cada evidencia; nunca se crean vacías ni con resultados ficticios.

## Privacidad de playtests (mínimo)
Solo testers que recluta y autoriza el propietario; ningún agente contacta a nadie. Se pide consentimiento antes de la sesión (y del tutor si el tester es menor). No se graban caras, voces ni nombres sin permiso expreso. Los resultados se guardan anonimizados (T1…T5) y sin datos de contacto. Los datos se borran si el tester lo pide.

## Fechas
El propietario preveía empezar el 2026-11-20 (Registro §12); el flujo real empezó antes: T00 se ejecutó y aprobó el 2026-11-17, y T01 empezó ese mismo día con autorización expresa.

## Cuestiones abiertas (historial: **resueltas** el 2026-11-17)
1. ¿El recurso de reanimación son los Cristales de Luz o un recurso aparte? → **D15**: Cristales de Luz.
2. ¿Cosméticos gratis por nivel? → **D16**: se sustituyen por recompensas no cosméticas; lo básico sigue gratis.
3. ¿Se renombra la «Luz» (XP)? → **D17**: Experiencia de Guardián (XP).
4. ¿Correspondencia de los 3 enemigos iniciales? → **D18**.
Sigue pendiente solo lo numérico: coste de reanimación y de autorreanimación, Cristales de Luz por partida y su fuente (balance; bloquea implementar D15, no diseñarlo).

## Relación T00–T21 ↔ TASK-001…012 (desglose histórico, no secuencia propia)
Las fichas TASK son **subtareas** de las Txx: conservan su estado y su historial, y **no se ejecutan por sí solas**. Una TASK solo es ejecutable si su Txx está autorizada por el propietario ([[ADR-007-revision-por-hitos]] §Estados). Las futuras TASK-013…031 de [[TASKS]] son desglose histórico que absorben las Txx indicadas; no crean otra secuencia de autorización.
| Txx | TASK reutilizadas y límite |
|---|---|
| T00 | Auditoría; sin TASK |
| T01 | Esta reconciliación; sin TASK |
| T02 | TASK-001 y base de TASK-002; **solo la infraestructura** de TASK-012 (overlay y comandos), **sin** mediciones con enemigos (dependen de TASK-005) |
| T03 | Biblia visual y especificaciones; sin TASK |
| T04 | Asset real de la Sombra Rastreadora (`.blend`, rig, export, clips en Studio) en un banco aislado; reutiliza solo parte de la lógica de TASK-005 y **no** la da por terminada. La lógica nunca sustituye a la aceptación artística Q2 |
| T05 | TASK-003, 004 (estados base de D5), 005, 006, 007, 008 y 009, y las mediciones de TASK-012. Prototipo con los 3 enemigos de D18. **Cierra con la decisión de validación de ADR-004** (§Puerta de validación) |
| T06 | Diseño de cartas; requisito previo de TASK-011 |
| T07 | TASK-011 (votación según [[Mecanicas]]), colección y equipamiento. Persistencia de inventario básica, no la robustez comercial de T12 |
| T08 | Diseño de enemigos y eventos; absorbe las futuras TASK-013/019 |
| T09 | Director procedural: amplía EnemyService/MatchService, sin duplicarlos |
| T10 | Salud, derribo, rescate, reanimación y expedición (amplía TASK-004). **Dueña única de TASK-010 (Foco Mayor)**, después de la puerta de ADR-004 |
| T11 | Economía y simulador Q3; diseño, no compras |
| T12 | Compras, recibos, DataStore y cosméticos; amplía la persistencia de T07 |
| T13 | Diseño final de UI/UX (distinto del UX temprano de T03) |
| T14 | UI funcional: amplía HUD, resultados y cartas de TASK-009/011 |
| T15 | Plan artístico de producción (distinto de T03 y del asset de T04) |
| T16 | Producción 3D final; reutiliza el asset de T04 |
| T17 | Audio y perfilado final; reutiliza las herramientas de TASK-012 |
| T18 | Tutorial, textos y marketing (diseño) |
| T19 | QA integrado: Q1, Q3 y Q4 con pruebas humanas reales |
| T20 | Aceptación integral |
| T21 | RC privada y restauración; publicar o vender requiere autorización expresa aparte |

## Puerta de validación de ADR-004 (ubicación y umbrales unificados)
- **Dónde:** la produce T05 (build del prototipo) y la decide el propietario. Sin esa decisión registrada **no se implementa nada de Fase 2**: T07, T09, T10, T12 y T14 quedan bloqueadas en su parte de código. Las tareas de diseño (T06, T08, T11, T13, T15) pueden avanzar.
- **Umbrales** (se toma el más exigente de los existentes, sin rebajar ninguno): los de [[VALIDACION-PROTOTIPO]] (≥ 5 externos, ≥ 2 en móvil, ≥ 2 en PC, ≥ 2 partidas cada uno) más los técnicos de [[MVP]] §Puerta 1 (FPS, partida completa, remotes validados). [[MVP]] y [[ROADMAP]] remiten aquí.
- **No es Q1:** Q1 (≥ 5 personas, 4/5 repetirían, etc.) es el gate final de la RC en T19/T20. Ninguno sustituye al otro.

## Consecuencias
Se actualizan [[GDD]], [[Mecanicas]], [[Monetizacion]], [[Progresion-Economia]], [[Modelo-Economico]], [[Decisiones-Monetizacion-Pendientes]], [[MVP]] y el índice. T01 no aprueba nada por su cuenta: requiere la revisión de Codex (`gpt-6-astra`, `high`).
