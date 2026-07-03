[README (1).md](https://github.com/user-attachments/files/29651017/README.1.md)
# Productividad de Picking · CD1 Petco

App de un solo archivo (`productividad-picking.html`) para revisar la productividad de los pikers por hora, comparada contra el objetivo de piezas por hora de cada pasillo.

## Cómo usarla

Hay dos formas de cargar los datos:

### Opción A — Subir el archivo (manual)
1. Abre `productividad-picking.html` en cualquier navegador (doble clic, o publícalo con GitHub Pages).
2. Exporta la hoja de Google Sheets como Excel: **Archivo → Descargar → Microsoft Excel (.xlsx)**.
3. Arrastra ese archivo a la app (o botón "Cargar archivo .xlsx").

### Opción B — Conectar en vivo con Google Sheets (recomendado)
Así la app siempre muestra los datos más recientes de tu Google Sheet, sin exportar nada a mano.

1. En el Google Sheet: botón **Compartir** → cambia a "Cualquier persona con el enlace" → rol **Lector**. (El archivo no se hace público en buscadores, solo queda accesible por quien tenga el enlace exacto.)
2. Da clic en la pestaña **Base** dentro del Sheet y copia el número que aparece después de `#gid=` en la URL del navegador.
3. Arma el enlace: `https://docs.google.com/spreadsheets/d/TU_ID_DE_ARCHIVO/export?format=csv&gid=EL_GID_DE_BASE`
   (tu ID de archivo es la parte larga entre `/d/` y `/edit` en la URL del Sheet)
4. Repite con la pestaña **Objetivo** para obtener su propio gid y su propio enlace.
5. En la app, botón **"Conectar Google Sheets"**, pega ambos enlaces y da clic en **Conectar y cargar**.
6. La próxima vez que abras la app recordará los enlaces y se conectará sola. El botón **Actualizar** vuelve a leer el Sheet al instante (útil después de una jornada de picking).

En ambos casos, todo el cálculo corre en tu navegador — el archivo/los datos nunca pasan por un servidor propio, así que es seguro para GitHub Pages.

## Qué calcula

- **Pasillo**: primeros 2 dígitos de `Ubic.proced.` (hoja Base, columna J).
- **Bloque hora**: cada fila se agrupa por `Usuarios` + `Fecha actual` + `Hora` (sin minutos).
- **Piezas pickeadas**: suma de `Ctd.real dest.` en ese bloque.
- **Pasillo del bloque**: el pasillo que más se repite dentro de ese bloque hora-usuario.
- **Objetivo/hr**: columna `piezas por hr` de la hoja Objetivo, para el pasillo del bloque.
- **% Productividad**: piezas pickeadas ÷ objetivo × 100.
- **Resumen diario**: suma piezas y objetivos de todos los bloques del día por usuario → % del día.

## Filtros

Fecha, Supervisor, Área, Pasillo y búsqueda por Usuario. Los filtros de **Supervisor** y **Área** se llenan automáticamente si completas esas columnas en la hoja **Objetivo** (columnas D y E) — actualmente están vacías en el archivo original, así que esos dos filtros aparecerán deshabilitados hasta que se llenen.

## Publicar en GitHub Pages

1. Sube `productividad-picking.html` a un repo (puedes renombrarlo `index.html` si quieres que sea la página raíz).
2. Activa GitHub Pages en Settings → Pages → selecciona la rama y carpeta.
3. Comparte el link — cada quien carga su propio archivo exportado, no hay datos guardados en el repo.
