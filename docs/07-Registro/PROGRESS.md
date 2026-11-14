---
tipo: registro
actualizado: 2026-11-14
etapa_actual: F (completada)
---
# Registro de progreso

> Reanudar aquí: **última etapa completada = F**. **Siguiente acción** = ver el final de la bitácora.

## Uso de modelos y agentes (registro verídico)

| Etapa | Trabajo | Agente / modelo realmente usado | Limitaciones |
|---|---|---|---|
| A | Estructura, CLAUDE.md, AGENTS.md, subagentes | Conversación principal: Sonnet 5.5 (medium) | Los archivos de `.claude/agents/` se crearon, pero **no se registran hasta reiniciar Claude Code** (error «Agent type not found»). |
| A | Plantillas Obsidian | Subagente `general-purpose` con `model: haiku`, `effort: low` (equivalente a `documentation-assistant`) | Sustituto del agente registrado. |
| B | Investigación de mercado y de políticas | Subagentes `general-purpose` con `model: sonnet`, `effort: medium` (equivalente a `market-researcher`) | Igual que arriba. |

## Entorno
- Git no está en el PATH de Windows ni en `C:\Program Files\Git`. Ver [[Como-trabajamos]] §Git.
- Vault: `Juego roblox 1/` copiado desde `juego roblox1/.obsidian/` (original conservado). El plugin Obsidian Git está presente pero **desactivado** (`community-plugins.json` vacío).

## Bitácora
- 2026-11-14 · Etapa A completada: carpetas, `.gitignore`, `templates.json`, 3 agentes, CLAUDE.md, AGENTS.md.
- 2026-11-14 · Etapa B: investigación (Sonnet medium ×2) → `02-Investigacion/`; 12 conceptos y matriz ponderada, escritos por la conversación principal (Sonnet medium).
- 2026-11-14 · Etapa C: revisión de finalistas con `model=opus`, `effort=medium` (agente general-purpose, no el registrado). Elegido Guardianes del Faro modificado → [[ADR-001-concepto]].
- 2026-11-14 · Etapa D: GDD y diseño (principal, Sonnet medium). Etapa E: arquitectura, ADR-002/003, roadmap, 12 tareas (TASK-001…012). Etapa F: auditoría → [[Auditoria-2026-11-14]].
- **Última etapa completada: F. Siguiente acción: el usuario aprueba concepto, instala Git/herramientas y lanza Codex con [[ENTREGA-PARA-CODEX]] (TASK-001).**
- 2026-11-14 · **Misión final:** Git 2.56.1 y Rokit 1.2.0 verificados (hacía falta refrescar el PATH de la terminal de Claude). `rokit init` + add/install → Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0; `rojo plugin install` copió `RojoManagedPlugin.rbxm`; pruebas en carpeta temporal OK. Creados `stylua.toml`, `selene.toml`, `.luaurc`; `.gitattributes` y `.gitignore` ampliados. Obsidian Git habilitado con ajustes seguros (sin automatismos). Concepto revisado (principal Sonnet medium, skill game-director) → [[Revision-Concepto]], [[VALIDACION-PROTOTIPO]], [[ADR-004-validacion-concepto]]. Tareas 001/002/004/006/008/012 ajustadas; [[ENTREGA-PARA-CODEX]] v2.
- **Subagentes (misión final):** `Agent` con `documentation-assistant` sigue devolviendo «not found». Causa probable: Claude Code solo carga el primer `.claude/agents/` tras reiniciar, y esta sesión se inició en `juego roblox1/`, no en `Juego roblox 1/`. Frontmatter validado contra la documentación oficial (`name`, `description`, `tools`, `model`, `effort` son válidos) mediante el agente `claude-code-guide` (Sonnet por defecto, lectura de docs). No se usaron Haiku ni Opus en esta misión.
- Haiku solo se usó realmente para las 4 plantillas; el resto de la documentación mecánica la escribió la conversación principal porque delegar costaba más que hacerlo.

- 2026-11-14 · **Mejora del vault (Sonnet 5.5, sin subagentes; el nivel de esfuerzo no se pudo verificar desde la sesión):** [[Home]] rediseñado con vistas Bases; snippet CSS `guardianes-dashboard`; `graph.json` con colores por carpeta; propiedades `tipo` y `fecha_actualizacion` en TASK-001…012 (estados intactos); Bases de tareas, registro, decisiones, errores, pruebas, recursos 3D e interfaces; [[Catalogo-3D]] (21 fichas, ninguna con modelo real); [[Interfaces]] (7 fichas, sin diseño en [[Figma]]); 5 Canvas; [[Centro-de-Control]]; [[Estado-de-Conexiones]]. Respaldo: `.obsidian-backup-2026-11-14/`. Sin commits ni push.

- 2026-11-14 · **Optimización funcional:** Home reducido a próxima tarea ejecutable, en curso, revisión y bloqueos + 6 accesos; [[Tareas-Ejecutables.base]] separa tareas ejecutables de las documentadas; [[Actividad-Real]] y plantilla [[entrega]] para avances verificados; Canvas y Base duplicados renombrados (`Mapa-Flujo-Claude-Codex.canvas`, `Tabla-Interfaces.base`); estado de GitHub unificado en [[Estado-de-Conexiones]]. Sin commits ni push.
