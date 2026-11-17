---
tipo: arquitectura
---
# Seguridad y prevención de exploits

Contexto: [[Cliente-Servidor]]. (Documentación oficial sobre FilteringEnabled/seguridad **no verificada** por investigación; se aplica el principio estándar de no confiar en el cliente.)

1. **Autoridad del servidor** sobre daño, Carga, enemigos, cartas, recompensas y persistencia.
2. **Validar toda entrada remota:** tipo, rango, finitud (`Vector3` con NaN/inf rechazados), pertenencia (el jugador solo actúa por sí mismo), estado válido, **limitador de tasa** por remote y jugador (`Util/RateLimiter`).
3. Un jugador que supere límites: ignorar y contar infracciones; tras umbral, registrar y (opcional, Beta) expulsar de la partida.
4. El cliente puede mentir sobre dirección del haz: aceptable (solo afecta su propia linterna); el servidor limita ritmo de giro y alcance.
5. No exponer en `ReplicatedStorage` datos que no deban conocerse (tablas de balance del servidor pueden ser públicas; semillas/lógica de recompensas no).
6. Economía: Experiencia de Guardián y Monedas del Faro solo las escribe `RewardService` al terminar una partida legítima, con límites por partida (máx. teórico por run). Los Cristales de Luz solo los gestiona el servidor durante la partida (MatchResourceService): consumo atómico, sin doble gasto y sin persistencia. Las pruebas de desconexión y doble consumo corresponden a T10.
7. Compras: `MarketplaceService.ProcessReceipt` idempotente, registrando `PurchaseId`; concesión validada; nunca confiar en el cliente.
8. DataStore: sesión bloqueada, reintentos con *backoff*, esquema versionado, no sobrescribir si lectura falló.
9. Anti-spam y privacidad: no registrar datos personales; respetar los requisitos de edad de Roblox ([[Politicas-y-Limites]]).
