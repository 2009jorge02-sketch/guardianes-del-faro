---
tipo: integracion
herramienta: Waspes 3D
estado_conexion: no verificada; sin acceso desde Claude
verificado: 2026-11-14
---
# Waspes 3D y Roblox Open Cloud

## Estado verificado
- En esta sesión **no hay ninguna herramienta ni conector de Waspes 3D** disponible para Claude, ni acceso a Roblox Open Cloud.
- No se han generado modelos, no se han consumido créditos, no se han creado claves API y no se han tocado permisos de Open Cloud.
- Si el servicio está configurado en Windows u otras herramientas, eso **no implica** que Claude pueda usarlo.

## Uso previsto
Generación o prototipado de modelos 3D según [[Flujo-de-Produccion]] (pasos 5-6). Ficha: `herramienta: waspes`.

## Reglas
1. **Cada generación consume créditos**: necesita autorización expresa del usuario, indicando recurso y límite.
2. Revisar licencias y condiciones de uso del contenido generado antes de integrarlo (riesgo R8, [[Riesgos]]).
3. Ningún resultado se da por bueno sin la revisión de geometría/materiales y los presupuestos de [[Rendimiento]].
4. Claves y tokens (Waspes, Roblox Open Cloud): **nunca en el vault ni en Git**; solo en variables de entorno o gestor de secretos del usuario.

## Pendiente
Confirmar con el usuario nombre exacto del servicio, plan de créditos y si existe API utilizable por Codex.
