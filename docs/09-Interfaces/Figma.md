---
tipo: integracion
herramienta: Figma
estado_conexion: conector autenticado (cuenta verificada); sin archivo del proyecto
verificado: 2026-11-14
---
# Figma

## Estado verificado (2026-11-14)
- El conector oficial de Figma está **disponible y autenticado** en la sesión de Claude: la consulta de identidad (`whoami`) respondió correctamente. Plan: equipo personal, nivel *starter*; el asiento aparece como **View**, por lo que **no está confirmado que se puedan crear o editar archivos**; hay que comprobarlo antes de prometerlo.
- **No se ha creado ni modificado ningún archivo de Figma** y no se ha enlazado ninguno al proyecto: no existe todavía el archivo «Guardianes del Faro».
- Capacidades que ofrece el conector (según sus herramientas): leer diseños y capturas, metadatos, variables, comentarios y Code Connect; crear diagramas en FigJam; escribir en un archivo. Solo se ha probado la identidad.

## Pendiente (acción del usuario)
1. Crear (o indicar) el archivo de Figma del proyecto y pegar su URL en `figma_archivo` de las fichas de [[Interfaces]].
2. Confirmar si el asiento permite edición (si no, solo lectura de diseños hechos por el usuario).

## Flujo
1. Claude define la pantalla en su ficha `UI-NNN` ([[interfaz]]).
2. El diseño visual se hace en Figma (usuario, o Claude si la cuenta lo permite y el usuario lo autoriza).
3. Se guarda en la ficha la URL del archivo (`figma_archivo`) y del frame (`figma_frame`).
4. Claude revisa el frame contra el [[GDD]] y [[Arte-UI-Audio]] y marca `estado_diseno: aprobado`.
5. Codex implementa con [[Especificacion-para-Codex]] y marca `estado_implementacion`.

Solo se consultan diseños que pertenezcan a este proyecto. Nunca guardar tokens de Figma en el vault.
