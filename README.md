# Geoportal Huancayo — demostración

Prototipo estático de MapLibre GL JS. Los polígonos son **simulados** y no constituyen datos oficiales ni delimitaciones reales.

## Publicación
1. Sube `index.html` a la raíz de un repositorio de GitHub.
2. En Netlify: Add new project → Import an existing project → GitHub.
3. Selecciona el repositorio. Build command: vacío; Publish directory: `.`.
4. Publica el sitio. Los siguientes commits se desplegarán automáticamente.

## Reemplazo de datos
En QGIS, exporta tus capas a GeoJSON en EPSG:4326. Reemplaza la variable `data` en `index.html` por una carga de GeoJSON, por ejemplo `fetch('./datos/urbano.geojson').then(r=>r.json())`, y conserva el campo numérico `period` con 2007, 2017 o 2025. Si tus capas son huellas acumuladas, conviértelas primero en anillos de expansión sin superposición mediante diferencia geométrica.

Nota: el mapa base de demostración de MapLibre no está destinado a tráfico de producción a escala. Para producción, usa un proveedor de teselas con condiciones y atribución adecuadas.
