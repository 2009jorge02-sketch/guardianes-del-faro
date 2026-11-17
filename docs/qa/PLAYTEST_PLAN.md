---
tipo: qa
gate: Q1
estado: NOT_VERIFIED
creado: 2026-11-17
tarea: T01 (plan); ejecución T19, validación T20; puerta temprana en T05
---
# Plan de playtest con personas reales (Q1 y puerta de ADR-004)

Contrato: [[ADR-006-contrato-producto-v4]] §Gates y §Puerta de validación. Fichas: [[Protocolo-Gates-Q]]. **Ningún agente recluta, contacta, graba ni publica nada**: lo hace o autoriza el propietario. Nunca se simulan testers con IA ni con bots.

## Dos pruebas distintas
| | Puerta de validación (ADR-004) | Q1 · RC privada |
|---|---|---|
| Cuándo | Fin de T05 (prototipo) | T19 (ejecución) y T20 (validación) |
| Mínimo | ≥ 5 externos; ≥ 2 en móvil y ≥ 2 en PC; ≥ 2 partidas cada uno ([[VALIDACION-PROTOTIPO]]) | ≥ 5 personas que no sean los agentes; ≥ 1 sesión en móvil y ≥ 1 multijugador (ideal 4); modos de 1, 2 y 4 jugadores si es posible |
| Umbrales | Los de [[VALIDACION-PROTOTIPO]] | 0 P0/P1 abiertos; ≥ 4/5 volverían a jugar; ≥ 4/5 entienden el objetivo tras el tutorial; ≥ 4/5 completan el onboarding sin ayuda |
| Si faltan testers | Fase 2 bloqueada en su parte de código | `WAITING_OWNER: HUMAN_PLAYTEST`; T19, T20 y T21 sin aprobación final |
Con 5 personas los datos son exploratorios, no estadísticos: no prometen retención ni ingresos.

## Consentimiento y privacidad
1. El propietario elige a los testers y obtiene su consentimiento (y el del tutor si el tester es menor) **antes** de la sesión, explicando qué se observa y cómo se guarda.
2. No se graban caras, voces ni nombres sin permiso expreso. Por defecto: notas escritas y capturas sin datos personales.
3. Los resultados se guardan anonimizados (T1…Tn) en `docs/qa/PLAYTEST_RESULTS_ANON.md`, sin contactos ni nombres de usuario.
4. Si un tester lo pide, sus datos se borran.

## Sesión (guion)
1. Build identificada por commit/SHA y semilla; dispositivo y modo anotados.
2. Sin explicar las reglas: el tester empieza la partida y el observador solo anota.
3. Tras 1–2 partidas, cuestionario breve.

## Métricas y preguntas
Duración real de la partida (mediana y extremos) · ¿entiende el objetivo y los controles sin ayuda? · ¿completa el tutorial/onboarding? · derribos, eliminaciones y sus causas · fallos de rescate o del minimapa · decisiones de expedición · ¿le parece justo? · **¿volverías a jugar? (sí/no y por qué)** · comprensión de Monedas del Faro y Robux en la tienda (solo desde T12) · FPS y dispositivo. Problemas clasificados P0–P3.

## Estado
**NOT_VERIFIED.** Aún no se ha hecho ninguna sesión ni hay testers confirmados.
