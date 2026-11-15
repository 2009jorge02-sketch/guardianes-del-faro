---
name: roblox-luau-engineer
description: "Implementa tareas aprobadas de Guardianes del Faro en Luau: arquitectura cliente-servidor, validación de remotos, módulos, Rojo, StyLua y Selene. Úsala al ejecutar una TASK-NNN que escribe o modifica código en src/ o tests/. No la uses para recursos 3D, interfaces visuales ni para depurar en Studio (hay skills propias)."
---

# roblox-luau-engineer

Implementa **solo** lo que pide una tarea aprobada. El diseño no se discute aquí: se sigue.

## Antes de escribir código (lectura progresiva)
1. `AGENTS.md` y `docs/00-Inicio/INDICE-IA.md` (si no los has leído en la sesión).
2. La tarea `docs/06-Tareas/TASK-NNN.md` **completa**. Comprueba que es ejecutable: `estado: lista` y todas las tareas de `depende_de` en `hecha` (`docs/05-Planificacion/Tareas-Ejecutables.base`). Si no, para y avisa.
3. De los documentos que enlaza la tarea, solo la sección citada. Fuentes habituales:
   - cifras de balance: `docs/03-Diseno/Mecanicas.md` (única fuente; van a `Config`, nunca como números sueltos en el código);
   - carpetas y servicios: `docs/04-Arquitectura/ARCHITECTURE.md`;
   - remotos y validación: `docs/04-Arquitectura/Cliente-Servidor.md` y `Seguridad.md`;
   - presupuestos: `docs/04-Arquitectura/Rendimiento.md`; enemigos: `docs/07-Registro/Decisiones/ADR-003-enemigos.md`.

## Reglas de ingeniería
- **El servidor es la autoridad.** El cliente solo envía intenciones; nunca decide daño, recompensas ni economía.
- **Todo `RemoteEvent`/`RemoteFunction` se valida en el servidor**: tipos, rangos, frecuencia (cooldown) y pertenencia. No confíes en nada que llegue del cliente.
- Módulos de responsabilidad única, sin globales, `--!strict` cuando sea posible. Nombres de código en inglés; comentarios breves.
- Enemigos sin `Humanoid` ni `Touched` masivos; pooling en lugar de crear/destruir en caliente (ADR-003).
- Sin funcionalidades fuera del alcance de la tarea. Si falta una decisión de diseño, anótala en «Bloqueos / preguntas» de la tarea y sigue con lo independiente.
- No instales herramientas ni dependencias; no hay Luau CLI (las pruebas se ejecutan en Studio, ver `docs/04-Arquitectura/Setup-Entorno.md`).

## Rojo y herramientas (comandos en la raíz del repo)
- `rojo build -o build/Guardianes.rbxl` y `rojo serve`; estructura objetivo en `ARCHITECTURE.md` §Estructura del repositorio.
- `stylua --check src tests` y `selene src` deben terminar sin avisos antes de cerrar la tarea.
- Si Rokit no ve las herramientas: abre terminal nueva o refresca el PATH (`Setup-Entorno.md`).

## Verificación antes de entregar
1. Recorre cada **criterio de aceptación** de la tarea y márcalo ✔/✘ con evidencia (comando y salida, medición o log). No marques lo que no has podido comprobar.
2. Ejecuta las pruebas indicadas en la tarea y los comandos de formato y lint.
3. Para depurar o medir en Studio usa la skill `roblox-playtest-debugger`.
4. Cierra según `AGENTS.md`: «Informe final» en la tarea, estado `en_revision`, `fecha_actualizacion`, entrada breve en `PROGRESS.md` y nota de entrega con la plantilla `entrega`.

## Límites
Sin commits a `main`, sin push, sin claves ni tokens en el repo. No toques `docs/` salvo lo que la tarea y `AGENTS.md` autorizan.
