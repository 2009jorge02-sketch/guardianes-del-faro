---
tipo: qa
estado: plantillas; los cuatro gates en NOT_VERIFIED
creado: 2026-11-17
tarea: T01
---
# Protocolo y fichas de los gates Q1–Q4

Umbrales: [[ADR-006-contrato-producto-v4]] §Gates. Política de revisión: [[ADR-007-revision-por-hitos]]. Cada entrega `Txx` incluye la matriz Q1–Q4 con uno de estos estados: `PASS`, `FAIL`, `NOT_APPLICABLE` (con justificación) o `NOT_VERIFIED`. **Solo es PASS con evidencia real enlazada**; quien no inspeccionó la build o el arte no puede marcar PASS.

## Ficha común (copiar al crear la evidencia; nunca crear fichas vacías)
```
gate: Q?        tarea: Txx         estado: NOT_VERIFIED
criterio/umbral: …
productor: (agente/modelo)   auditor del hito: H?
build/commit/SHA: …   semilla: …   dispositivo: …
procedimiento seguido: …
evidencias (rutas): …
mediciones: …
defectos (P0–P3): …
decisión y fecha: …
```

## Q1 · Personas reales → [[PLAYTEST_PLAN]]
Evidencia: `docs/qa/PLAYTEST_RESULTS_ANON.md`. Productores: T05 (puerta temprana) y T19; validación en T20.

## Q2 · Arte en Roblox → `docs/qa/VISUAL_SCORECARD.md` (se crea en T03)
- Rúbrica de 100 puntos: silueta/proporciones 25 · formas/modelado/materiales 20 · iluminación/paleta 15 · animación/telegraphing 25 · VFX/legibilidad 15. Umbral: ≥ 85 global y ≥ 70 % en cada dimensión.
- Evidencias por activo: `.blend` original, export (`.fbx` u otro compatible), capturas en Studio desde ángulos comparables con su referencia de [[Indice-Referencias-Visuales]], vídeo de idle/movimiento/ataque/impacto/muerte (jefes: entrada y fases), control en móvil y puntuación del ejecutor **ratificada por el auditor del hito**.
- El rendimiento se evalúa aparte: no se cambian FPS por puntos de arte. No se puntúan conceptos ni renders de Blender.
- Inventario de activos: `docs/qa/ASSET_MANIFEST.md` (ruta, hash, licencia, fuente).

## Q3 · Economía → `docs/qa/ECONOMY_SIMULATION.md` (se crea en T11)
- Modelo editable y reproducible (CSV/JSON + script local o tabla con fórmulas).
- Entradas: Monedas del Faro por victoria y derrota, duración, % de victorias, bonus, cartas por rareza, precios en Monedas y en Robux, % de compradores, gasto medio, tipo de cambio y DevEx vigentes (citados).
- Escenarios: gratis/comprador; nuevo/habitual/muy activo; victorias 30/50/70 %; conversión 1/3/5 %; gasto 50/180/350 R$; las 5 rarezas; objetivos 100/200/300/1 000 €. Base D11: 0,907 €/USD y 180 R$; sensibilidad 0,86 y 250 R$.
- Salidas: partidas y horas por carta (mediana y rango), jugadores/mes por objetivo. Umbrales: primera común en ≤ 10 partidas; primera legendaria en ≈ 12–20 h (D4). La V0.1 da ≈ 41–58 h: **pendiente de corregir en T11**.

## Q4 · Recuperación → `docs/qa/RESTORE_DRILL.md` (se crea en T02)
- **Preflight antes de cada tarea con cambios:** rama, SHA base, `git status`, diff pendiente y `backup_id` con ubicación, manifiesto SHA256 y fecha. Debe incluir lo no versionado (docs, `.blend`, texturas, exports, configuración). Nunca se copian secretos.
- **Ensayo (T02):** restaurar en una carpeta aislada HEAD, lo no versionado y un activo Blender; ejecutar lint/tests; comparar hashes; confirmar que el original no cambió. Adjuntar comandos, salidas y comparación.
- Se repite el preflight antes de T04/T07/T09/T12/T16/T19/T21 y la restauración completa antes de cerrar T21. Si falla: `BLOCKED`, sin migraciones destructivas.
- Primer preflight real: `T01-preflight-20261117T1620Z` (ver [[T01-Entrega-Parcial-2026-11-17]]); está en el mismo disco y sin ensayo de restauración.

## Estado actual
| Gate | Estado |
|---|---|
| Q1 | NOT_VERIFIED |
| Q2 | NOT_VERIFIED |
| Q3 | NOT_VERIFIED |
| Q4 | NOT_VERIFIED |
