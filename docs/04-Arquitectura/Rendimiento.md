---
tipo: arquitectura
estado: presupuestos propuestos (a medir; objetivos móviles de Roblox [PV])
---
# Rendimiento

Riesgo principal del proyecto (R1 en [[Riesgos]]). Contexto: [[Politicas-y-Limites]] (texturas ≤512², streaming).

## Presupuestos objetivo (propuestos)
| Métrica | Objetivo |
|---|---|
| FPS móvil de gama baja | ≥30 con 60 enemigos + 4 jugadores |
| FPS PC | ≥60 |
| Enemigos simultáneos | ≤60 (tope duro en `Config`) |
| Triángulos/enemigo | ≤2 000; instancias por enemigo ≤5 |
| Luces dinámicas activas | ≤6 (haces: 1 por jugador + foco); sin sombras en tiempo real salvo Faro |
| Tráfico de red por jugador | señales de haz ≤20 Hz, sin enviar posiciones de enemigos si se usa BulkMoveTo |
| Memoria de texturas | ≤512² por textura; atlas compartidos |

## Técnicas previstas
- Enemigos **sin `Humanoid`**; movimiento por `workspace:BulkMoveTo` por lotes a 15–20 Hz con interpolación visual en cliente cuando haga falta.
- **Pooling** de enemigos, partículas y proyectiles (`Util/Pool`); no crear/destruir en caliente.
- Cálculo de impactos del cono con matemática vectorial sobre una tabla de posiciones (no `Raycast` por enemigo); oclusión no necesaria (mapa abierto).
- Cuantizar actualizaciones; evitar `Touched` masivos (colisión con faro por distancia al cuadrado).
- Efectos con `ParticleEmitter` ligeros y opción «reducir efectos».
- Mapa pequeño; sin `StreamingEnabled` necesario en MVP.

## Medición
[[TASK-012]]: overlay de FPS/ping/nº de enemigos, comando para fijar nº de enemigos (50/100/200) y registrar resultados en `docs/07-Registro/Revisiones/`. **Si no se alcanzan 30 FPS móvil con 60 enemigos, activar el fallback de [[ADR-003-enemigos]] o reducir el tope.**
