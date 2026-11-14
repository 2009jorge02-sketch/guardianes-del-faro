---
tipo: diseno
estado: dirección; no se generan assets definitivos todavía
---
# Arte, interfaz y audio

## Dirección artística
- **Estilo:** low-poly estilizado, formas redondeadas, materiales mate con brillo cristalino en las Sombras. Legibilidad > detalle.
- **Paleta:** noche azul tinta (#0B1630, #1B2A4E), luz cálida ámbar (#FFC15E), Sombras violeta-turquesa de cristal (#6A4FB3, #2FC4B2), mar espuma (#9FD6E8). Contraste luz/sombra como lenguaje principal.
- **Iluminación:** pocas luces dinámicas (rendimiento móvil); el haz = `SpotLight`/parte neón ligera con `Beam`/malla de cono, no sombras en tiempo real salvo en el Faro. Bruma baja con `Atmosphere`.
- **Modelos a crear (más adelante, Blender/Studio):** Faro modular (base, torre, galería, lámpara), isla (roca, hierba, muelle, rocas), 3 Sombras + Bruto + Gaviota + jefe, linternas (3 variantes), mascotas (3).
- **Presupuesto:** malla ≤2 000 triángulos por enemigo, texturas ≤512² ([[Politicas-y-Limites]]), 1 material compartido por familia.
- **Animaciones:** Sombras con ciclo simple por transformaciones (sin rigs complejos), idle/caminar del jugador por defecto de Roblox, recoil de linterna, giro del foco.
- **Efectos (VFX):** destello al romper una Sombra (partículas de cristal, pool), grieta del escudo del Bruto, chispas en el Faro al dañarse, relámpagos lejanos.

## Feedback
Cada impacto de luz: parpadeo blanco en la Sombra + tick sonoro suave y tono ascendente; Faro dañado: sacudida de cámara leve, silueta roja en HUD; fin de noche: amanecer (gradiente 3 s) y fanfarria breve.

## Interfaz (conceptual)
- **Menú principal:** Jugar (1 botón), Personalizar, Tienda, Ajustes. Fondo: faro bajo tormenta.
- **HUD:** barra Integridad del Faro (arriba centro), «Noche N/5» y temporizador, barra de Carga (junto al botón de linterna), contador de Sombras destruidas, iconos de cartas activas.
- **Selección de carta:** 3 tarjetas grandes, 15 s, con previsualización de efecto.
- **Resultados:** noches superadas, estadísticas, Cristales/Luz ganados con barra de nivel, «Otra partida».
- **Personalización/Tienda:** rejilla por categorías (linterna, haz, faro, mascota, título); sin ventanas emergentes de venta.
- **Ajustes:** volumen, sensibilidad, asistencia de apuntado, **modo daltónico** (formas además de color), reducir efectos.
- **Notificaciones:** discretas; sin spam de ofertas.
- Accesibilidad y dispositivos: botones ≥48 px, texto ≥16 px equivalente, soporte teclado/ratón, táctil y mando.

## Audio
Mar y viento ambiente; melodía de piano/cuerdas tensa en noche, cálida en intermedio; SFX: linterna (zumbido eléctrico), cristal roto, faro (bocina grave al ser dañado). Banda sonora e SFX con licencia libre o generados: **pendiente de decisión** (ver [[Riesgos]]). Usar audio de la biblioteca de Roblox/Creator Store con licencia verificada.

## Relacionado (añadido en la mejora del vault)
- Catálogo de recursos 3D: [[Catalogo-3D]] · Fichas de pantallas y Figma: [[Interfaces]] · [[Figma]]
