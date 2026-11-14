---
id: ADR-004
titulo: Concepto provisional sujeto a validación de prototipo
estado: aceptada
fecha: 2026-11-14
decide: usuario (aprobación provisional) + Claude (plan)
---
# ADR-004 · Validación del concepto

## Contexto
El usuario aprueba [[ADR-001-concepto]] **solo de forma provisional**. [[Revision-Concepto]] concluye que es viable para prototipo, con la profundidad como mayor incertidumbre.

## Decisión
1. Invertir solo en la Fase 1 hasta ejecutar [[VALIDACION-PROTOTIPO]].
2. Incluir en el prototipo controles táctiles A/B y el parámetro `overlapBonus` (desactivado por defecto) para poder probarlos.
3. Decisión continuar / modificar / descartar tras el playtest; se registrará en un ADR nuevo.

## Consecuencias
Fase 2 (TASK-010 en adelante) queda congelada hasta esa decisión. Alternativas de reserva: [[Ideas-Evaluadas]].

## Riesgos
Muestra pequeña ⇒ señal cualitativa; retención real solo se medirá en Beta.
