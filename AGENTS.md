# AGENTS.md — Instrucciones para Codex

Eres el responsable de **programar, construir, probar y optimizar** el videojuego de Roblox. Claude diseña y planifica; tú ejecutas. No hay conexión automática entre ambos: la coordinación es por archivos de este repositorio (vault de Obsidian) y Git/GitHub.

## Antes de empezar (lectura progresiva, sin cargar todo)
1. Este archivo y `docs/00-Inicio/INDICE-IA.md` (índice ligero: qué leer para cada necesidad).
2. **Tarea asignada: lee `docs/06-Tareas/TASK-NNN.md` COMPLETA** (objetivo, requisitos, dependencias, criterios de aceptación, pruebas, restricciones). No empieces sin haberla leído entera.
3. Dependencias: comprueba solo el `estado` (YAML) de cada tarea de `depende_de`; todas deben estar `hecha`. Una tarea «lista» con dependencias sin hacer es solo documentación, no ejecutable (vista `docs/05-Planificacion/Tareas-Ejecutables.base`).
4. Documentos enlazados por la tarea (`Contexto`, `Requisitos`, `Restricciones`): lee **solo la sección citada** y no repitas lecturas ya hechas.
5. `docs/00-Inicio/ENTREGA-PARA-CODEX.md` solo en tu primera sesión; `docs/07-Registro/PROGRESS.md` solo las últimas líneas.
6. Si no hay instrucción distinta, toma la primera tarea ejecutable (`lista` con dependencias `hecha`).
Si hay MCP de Obsidian, úsalo para buscar y leer fragmentos; si no, lee archivos con rango de líneas.

## Entorno (verificado 2026-11-14; detalle en `docs/04-Arquitectura/Setup-Entorno.md`)
- Git, Rokit 1.2.0, Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0 y el plugin de Rojo están instalados (versiones en `rokit.toml`). Ejecuta los comandos **dentro del repo**; si la terminal no ve `git` o `rokit`, refresca el PATH o abre una nueva.
- Antes de cerrar cualquier tarea: `stylua --check src tests` y `selene src` sin avisos.
- No hay Luau CLI ni luau-lsp: no los instales sin autorización; las pruebas se ejecutan desde Studio hasta nueva decisión.
- **El concepto es provisional** (ADR-004): solo la Fase 1 hasta ejecutar `VALIDACION-PROTOTIPO.md`. No empieces TASK-010 en adelante sin que su estado sea `lista`.
- No hagas push ni crees remotos; commits solo si el usuario lo pide o en la rama de tarea (sección Git). Estado real de GitHub: `Estado-de-Conexiones.md`.

## Reglas de trabajo
1. Respeta el GDD y la arquitectura (`ARCHITECTURE.md`). No rediseñes el proyecto ni añadas funcionalidades fuera del alcance de la tarea.
2. Código Luau limpio, modular y seguro: el **servidor es la autoridad**; el cliente nunca decide recompensas, daño ni economía; valida todo `RemoteEvent`/`RemoteFunction` en el servidor (tipos, rango, cooldown, propiedad).
3. Ejecuta las pruebas de la tarea y las herramientas del repo. No instales herramientas ni dependencias sin ADR aprobado.
4. Si falta una decisión de diseño imprescindible: detén esa parte, anótala en «Bloqueos / preguntas» de la tarea y en `PROGRESS.md`, y continúa con lo independiente.
5. No cierres una tarea sin evidencias (pruebas, capturas o logs descritos).
6. Nunca guardes claves API ni tokens en el repo ni en el vault.

## Ciclo y estados
Claude planifica → Codex ejecuta → Codex documenta → Claude revisa → Codex continúa.
Estados (`estado` del YAML): `borrador` → `lista` → `en_progreso` → `en_revision` → `hecha` (solo Claude, tras revisar) | `bloqueada`.
- Al empezar: `en_progreso`. Al terminar: rellena «Informe final» de la tarea, `en_revision`, y añade una entrada breve en `PROGRESS.md`.
- Cada cambio de estado actualiza también `fecha_actualizacion`. `depende_de` es el campo de dependencias.
- Crea `docs/07-Registro/Entregas/ENT-TASK-NNN.md` con la plantilla `entrega` (rama, commit, `verificacion: sin_verificar`). Claude la marca `verificada` o `rechazada`; solo lo verificado cuenta como avance.

## Git
Rama por tarea `codex/task-NNN-slug`; commits con prefijo `TASK-NNN:`; sin push a `main`; PR cuando exista remoto.

## Informe final (en la tarea; resumen en PROGRESS)
Qué se hizo · archivos · pruebas y resultado · criterios (✔/✘ con evidencia) · problemas y bloqueos · siguiente paso.

## Otros registros
Errores: `docs/07-Registro/Errores/ERR-NNN.md` (plantilla `error`); pruebas: `docs/07-Registro/Pruebas/`. Recursos 3D: ficha `RES-NNN` (rellenar archivos y estados solo con evidencia; sin binarios grandes en Git, ver `docs/08-Recursos-3D/Estructura-de-Archivos.md`). Interfaces: ficha `UI-NNN` y `docs/09-Interfaces/Especificacion-para-Codex.md`.

## Convenciones de código
Luau con `--!strict` cuando sea posible; módulos de responsabilidad única; sin variables globales; nombres en inglés para código y comentarios breves; documentación del proyecto en español.
