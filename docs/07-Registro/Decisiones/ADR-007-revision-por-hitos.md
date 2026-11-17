---
id: ADR-007
titulo: Política de eficiencia V4.2 — autorrevisión por tarea y cuatro auditorías cruzadas por hito
estado: aceptada
fecha: 2026-11-17
decide: usuario (política V4.2) + Claude (redacción)
sustituye: cláusulas de revisión cruzada por tarea del contrato V4.1 (matriz «22 tareas y 22 revisiones», «revisión independiente» de cada Txx y «no aprobar sin la revisión de la otra IA») y la columna «Revisión» de la matriz de modelos
---
# ADR-007 · Revisión por hitos (V4.2)

## Contexto
El contrato V4.1 (`01_PLAN_MAESTRO_22_TAREAS.md`, `02_PROMPT_MAESTRO_CODEX.md`, `03_PROMPT_MAESTRO_CLAUDE_CODE.md`, externos al repo y **no editados**) exigía una revisión cruzada de la otra IA tras cada una de las 22 tareas. El propietario la sustituye para reducir consumo sin rebajar la calidad. Este ADR prevalece sobre esas cláusulas; el resto del contrato V4.1, [[ADR-006-contrato-producto-v4]] y el historial siguen vigentes.

## Decisiones
1. **Se mantienen las 22 tareas T00–T21**, con su orden, ejecutor y criterios de aceptación.
2. **Autorrevisión por tarea:** el ejecutor revisa y comprueba su propia tarea. Según corresponda: tests automáticos, análisis estático (StyLua/Selene/luau-lsp), integración en Studio y enlaces/YAML en el vault. Cada entrega `Txx` incluye diff o lista de archivos, comandos con su salida real, criterios comprobados uno a uno, la matriz Q1–Q4 (PASS / FAIL / NOT_APPLICABLE / NOT_VERIFIED) y los riesgos pendientes. Estado final de la tarea: `SELF_VERIFIED`. No equivale a «auditada».
3. **Cuatro auditorías cruzadas estratégicas.** Cada una la hace el otro proveedor sobre las tareas que no ejecutó, en una sola pasada. Revisa el conjunto de cambios desde el hito anterior (diff entre commits o snapshots), los resultados de las pruebas y los riesgos pendientes. **Cortes y criterios de aceptación** (definidos en T01 por encargo del propietario y **confirmados por el propietario el 2026-11-17**):
   | Hito | Tareas | Momento | Criterios mínimos para `APPROVED` |
   |---|---|---|---|
   | H1 · Base técnica | T00–T04 | Tras T04 | Documentación coherente con ADR-006/007 y sin enlaces rotos; proyecto Rojo y lint/format en verde (StyLua, Selene); **ensayo de restauración Q4 superado en una copia aislada (T02)**; rúbrica Q2 fijada (T03); primera Sombra con `.blend`, export, clips y capturas en Studio con ≥ 85/100 y ≥ 70 % por dimensión (T04); sin secretos en el repo |
   | H2 · Bucle jugable | T05–T10 | Tras T10 | Partida de 5 noches completa en solitario y con 2–4 jugadores locales sin errores; ≥ 30 FPS con 60 enemigos en el dispositivo acordado; remotes validados en servidor ([[Seguridad]]); derribo, rescate, reanimación y expedición con estados autoritativos y pruebas de desconexión/doble consumo; **decisión de la puerta de ADR-004 registrada**; semilla reproducible |
   | H3 · Progresión y monetización | T11–T14 | Tras T14 | Simulador Q3 reproducible con todos sus escenarios; primera legendaria ≈ 12–20 h (D4) o desviación aprobada; compras **solo en sandbox o con moneda ficticia** (ProcessReceipt idempotente, sin doble cobro ni pérdida); DataStore con migraciones y restauración de datos de prueba; misma carta por ambas vías; ninguna venta de reanimaciones ni de Cristales de Luz; precios regionales dinámicos |
   | H4 · Auditoría final | T15–T21 | Antes de cerrar T21 | Q1 con personas reales (o `WAITING_OWNER: HUMAN_PLAYTEST`), Q2 en todos los enemigos críticos y jefes, Q3 sobre la tienda final y Q4 con restauración completa de la RC; cero P0/P1 abiertos; nada publicado ni vendido sin autorización expresa |
   Una tarea `SELF_VERIFIED` puede servir de base a la siguiente; el hito no se cierra hasta tener `APPROVED` en su auditoría. Un `CHANGES_REQUESTED` se corrige con `Txx-fix`, que se autorrevisa y vuelve a la auditoría del hito.
4. **Revisión extraordinaria obligatoria:** ante un problema crítico de seguridad, integridad de datos, monetización o arquitectura, se detiene la tarea, se registra y se pide revisión al otro proveedor o una decisión del propietario. No se sigue hasta resolverlo.
5. **Modelos:** la matriz de modelos de V4.1 deja de ser obligatoria por tarea. Se usa el modelo de menor coste capaz de ejecutar bien cada tarea, sin máximo razonamiento en cambios triviales o repetitivos. Los modelos de mayor capacidad se reservan para arquitectura compleja, bugs difíciles y las auditorías H1–H4. **Ningún agente cambia de modelo por su cuenta** si el cambio requiere selección manual o autorización: lo propone y lo decide el propietario. Se registran el modelo y el esfuerzo realmente usados.
6. **Contexto:** se trabaja con resúmenes de estado, diffs, tests y documentos canónicos. No se releen documentos que no han cambiado ni se repiten investigaciones, auditorías o tareas terminadas sin un motivo verificable.
7. **Se conservan:** reparto Claude/Codex, decisiones D1–D18, las 12 referencias visuales, los ADR, Git/Obsidian, backups preflight Q4, `PROGRESS.md`, un solo escritor por archivo y el control de cuota semanal de Claude hasta que se confirme el Free Reset.
8. **Gates Q1–Q4:** sin cambios; siguen en NOT_VERIFIED hasta tener evidencia real. Sus verificaciones se reparten entre las tareas previstas y las auditorías de hito.

## Estados
| TASK (YAML) | Contrato | Regla |
|---|---|---|
| `borrador`, `lista` | `NOT_STARTED` | `lista` solo indica que la ficha está preparada. Una TASK es ejecutable solo con `txx_autorizada: true`, que se activa cuando el propietario autoriza su Txx ([[Tareas-Ejecutables.base]]) |
| `en_progreso` | `IN_PROGRESS` | — |
| `en_revision` | `SELF_VERIFIED` o `READY_FOR_REVIEW` | Entrega con evidencias; si hay auditoría pendiente, `READY_FOR_REVIEW` |
| `hecha` | `APPROVED_INTERNAL_V4.2` y, al cerrar su hito, `APPROVED` | Nunca por conversión automática: exige autorrevisión con evidencias. `APPROVED` exige la auditoría del hito |
| `bloqueada` | `BLOCKED` | Con motivo registrado |
| — | `CHANGES_REQUESTED` | Registrado en la revisión o auditoría; no equivale a `borrador` |
| — | `WAITING_OWNER`, `WAITING_MODEL_CHANGE` | Se anotan como motivo y se conserva el estado de trabajo |
`APPROVED_INTERNAL_V4.2` = cerrada por autorrevisión según esta política; **no es una aprobación independiente**.

## Aplicación inmediata
- T00: APPROVED; no se repite.
- T01: se completa con autorrevisión y controles documentales (enlaces, YAML, coherencia con ADR-006), **sin** auditoría cruzada individual. Entra en H1.
- D15–D18: registradas en [[ADR-006-contrato-producto-v4]] con el texto del propietario.
- La revisión preliminar de Codex de T01 (CHANGES_REQUESTED — PRELIMINAR) queda como evidencia; sus observaciones se cierran una a una en [[T01-Entrega-Parcial-2026-11-17]].

## Consecuencias
Menos consumo y menos esperas entre tareas; a cambio, más riesgo de que un error se propague dentro de un hito. Lo mitigan la autorrevisión con evidencias, la revisión extraordinaria y la auditoría por diff acumulado. `AGENTS.md` y `CLAUDE.md` deben enlazar esta política en el siguiente tramo de T01.
