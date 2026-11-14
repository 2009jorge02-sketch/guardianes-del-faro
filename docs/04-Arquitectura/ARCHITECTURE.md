---
tipo: arquitectura
version: 0.1
estado: propuesta para el prototipo y MVP
---
# Arquitectura técnica

Diseño: [[GDD]], [[Mecanicas]]. Detalle: [[Cliente-Servidor]], [[Seguridad]], [[Rendimiento]]. Decisiones: [[ADR-002-herramientas]], [[ADR-003-enemigos]].

## Herramientas (instaladas)
Rokit 1.2.0 → Rojo 7.7.1, StyLua 2.6.0, Selene 0.32.0; plugin de Rojo copiado. Configs ya en la raíz: `rokit.toml`, `stylua.toml`, `selene.toml`, `.luaurc`. Detalle y comandos: [[Setup-Entorno]]. Validación del concepto antes de ampliar: [[VALIDACION-PROTOTIPO]].

## Estructura del repositorio (Rojo, propuesta)
```
default.project.json
selene.toml · stylua.toml · .luaurc (strict)
src/
  shared/    → ReplicatedStorage.Shared
    Config.luau      (TODOS los valores de balance; fuente: Mecanicas.md)
    Types.luau       (tipos Luau)
    Remotes.luau     (definición y creación de remotes)
    Util/            (Signal, Math, Pool, RateLimiter)
  server/    → ServerScriptService.Server
    Main.server.luau (arranque: inicia servicios en orden)
    Services/        (MatchService, LighthouseService, EnemyService, BeamService,
                      SpotlightService, CardService, PlayerStateService,
                      MapBuilder, [Fase 2: DataService, RewardService, ShopService])
  client/    → StarterPlayer.StarterPlayerScripts.Client
    Main.client.luau
    Controllers/     (InputController, BeamController, HudController,
                      CardController, FxController, CameraController)
tests/       (pruebas Luau/TestEZ-lite; ver TASK-001)
docs/        (esta documentación)
```
Servicios y controladores son módulos con `Init()` y `Start()`; sin globales; dependencias por `require` explícito. Un módulo = una responsabilidad.

## Servicios del servidor
| Servicio | Responsabilidad |
|---|---|
| MatchService | Máquina de estados: `Lobby → Prep → Night(1..5) → Intermission → Victory/Defeat → Results` |
| LighthouseService | Integridad, daño recibido, mejoras de Faro |
| EnemyService | Pool, spawn por noche (datos), movimiento por lotes, vida, tope 60 |
| BeamService | Valida entrada de linterna, Carga, cálculo de impactos cono→enemigos |
| SpotlightService | Foco Mayor (ocupación, modo auto/manual) |
| CardService | Ofertas, votos, aplicación de efectos |
| PlayerStateService | «Apagado», inmunidad, spawn |
| MapBuilder | Genera la isla greybox por código |
| DataService (Fase 2) | Persistencia (DataStore con sesión bloqueada y reintentos) |
| RewardService (Fase 2) | Luz y Cristales al terminar la partida |

## Cliente
Entrada, visuales del haz, HUD, cámara, efectos y audio. **El cliente nunca decide daño, recompensas, estado de partida ni economía.**

## Comunicación
Remotes definidos en `Shared/Remotes` (ver [[Cliente-Servidor]]). El estado de partida se replica por `RemoteEvent` de cambio de estado y atributos de `ReplicatedStorage`/`Workspace` mínimos.

## Persistencia (Fase 2)
Un perfil por jugador: `{ version, luz, cristales, desbloqueos, equipado, estadisticas }`. DataStore con reintentos y bloqueo de sesión; guardar al terminar partida y al salir; esquema versionado con migraciones. Respetar límites ([[Politicas-y-Limites]]).

## Errores
`pcall` en I/O (DataStore, Marketplace); registro con prefijo `[Faro]` y niveles; si falla el guardado, reintentar y avisar discretamente sin perder la partida.

## Estrategia de pruebas
1. Pruebas unitarias de módulos puros (Config, cálculos de cono, escalado de oleadas). **No hay Luau CLI instalado**: de momento se ejecutan desde Studio con un script de pruebas; un CLI requiere autorización ([[ADR-002-herramientas]]).
2. Pruebas manuales guiadas en Studio (Play Solo, Local Server con 2–4 clientes) descritas en cada `TASK`.
3. Perfilado: comandos de depuración + overlay de FPS/ping/enemigos ([[TASK-012]]); prueba en móvil real o emulador.
4. Revisión por Claude según criterios de aceptación ([[AGENTS]] ciclo).

## Compatibilidad de dispositivos
PC, móvil, tablet, mando. Entrada abstracta en `InputController` (acciones, no teclas). UI con `UIScale`/anclajes.

## Relacionado (añadido en la mejora del vault)
- Dependencias entre tareas: [[Arquitectura-de-Sistemas.canvas]] · Estado de conexiones: [[Estado-de-Conexiones]]
