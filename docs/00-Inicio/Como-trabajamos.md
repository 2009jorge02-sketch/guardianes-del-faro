---
tipo: guia
actualizado: 2026-11-14
---
# Cómo trabajamos

## Herramientas y roles
- **Claude Code**: investiga, diseña, planifica, revisa ([[CLAUDE]]).
- **Codex**: programa, prueba, optimiza ([[AGENTS]]).
- **Obsidian**: panel y documentación (este vault). **GitHub**: versiones.
- No hay conexión automática Claude↔Codex: se coordinan por archivos y GitHub.

## Ciclo
Claude planifica → Codex ejecuta → Codex documenta → Claude revisa → Codex continúa. Estados: `borrador → lista → en_progreso → en_revision → hecha | bloqueada`.

## Cómo abrir el vault
1. Obsidian → *Abrir carpeta como bóveda* → `C:\Users\tatia\Documents\juego roblox1\Juego roblox 1`.
2. Abrir [[Home]]. Si Obsidian pide confiar en el vault, acepta (el plugin Git está activado con ajustes seguros, ver abajo).
3. El vault anterior (`juego roblox1\.obsidian`) se conserva sin cambios.

## Git
- Estado de Git y GitHub: ver [[Estado-de-Conexiones]] §GitHub (fuente única). Todo lo creado tras el commit inicial está sin commit (`git status`).
- Las terminales abiertas antes de instalar Git no ven el PATH nuevo: abre una terminal nueva ([[Setup-Entorno]]).
- Claude y Obsidian Git no hacen commits ni push automáticos; los haces tú (o Codex en su rama de tarea, según [[AGENTS]]).
- **Obsidian Git:** el plugin quedó habilitado en `.obsidian/community-plugins.json` con ajustes seguros (`.obsidian/plugins/obsidian-git/data.json`: sin auto-commit/pull/push, push desactivado). Si Obsidian estaba abierto, ciérralo y ábrelo de nuevo; si pide «Modo restringido», pulsa *Ajustes → Complementos de la comunidad → Activar complementos de la comunidad* y comprueba que «Git» está activado.

## Modelos
Principal: Sonnet 5.5 (medium). Subagentes en `.claude/agents/` (Haiku low, Sonnet medium, Opus medium). **Tras reiniciar Claude Code** se registran `documentation-assistant`, `market-researcher` y `strategic-reviewer`; en esta primera sesión se emularon con `general-purpose` y parámetros `model/effort` ([[PROGRESS]]).

## Convenciones de documentación
Español; YAML en cada nota; enlaces internos de Obsidian (doble corchete); una fuente de verdad por dato; ADR para decisiones; plantillas en `docs/_plantillas` (Obsidian → Insertar plantilla).
