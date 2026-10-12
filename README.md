# Geoportal - Prototipo

Geoportal multiciudad para explorar resultados de análisis territorial. Desarrollado con MapLibre GL JS, HTML, CSS y JavaScript; publicable como sitio estático en Netlify.

## Publicación

Subir **todos** los archivos y carpetas a la raíz del repositorio GitHub, manteniendo la estructura. En Netlify: build command vacío, publish directory `.`. No abrir index.html con doble clic: `config.json` se carga mediante HTTP.

## Incorporar datos reales desde QGIS

1. Exportar las capas a GeoJSON en **EPSG:4326 (WGS 84)**.
2. Preparar polígonos de **periodos no superpuestos** (2007: huella inicial; 2017: solo expansión 2007–2017; 2025: solo expansión 2017–2025). Esto evita contabilizar áreas dos veces.
3. Cada entidad debe tener `properties.period` numérico (2007, 2017, 2025) y opcionalmente `properties.name`.
4. Guardar el GeoJSON en `datos/` y actualizar la ruta `geojson` de la ciudad en `config.json`. Cambiar `demo` a `false`, `source` a la fuente oficial y ajustar `years`.
5. Para agregar una ciudad, duplicar una entrada del arreglo `cities` y configurar `id`, `name`, `center` [longitud, latitud], `zoom`, `years`, `geojson`, `source` y `powerbi` (opcional).

Los indicadores de superficie se calculan en el navegador a partir de las geometrías mediante una aproximación plana; **no son adecuados para reportes oficiales**. Para producción, calcular hectáreas y tasas en QGIS con un CRS proyectado apropiado, validar topología y almacenar indicadores auditados. La descarga incluye únicamente las entidades visibles, según periodo y visibilidad de capa.

## Mapas base y atribución

Se usan estilos de CARTO para la demostración. Antes de una publicación institucional, comprobar las condiciones y límites vigentes del proveedor y conservar las atribuciones visibles en el mapa. MapLibre es software libre, pero los servicios de teselas tienen sus propias condiciones. No se incluye mapa satelital porque requeriría elegir un proveedor y sus credenciales/condiciones.

## Alcance de la versión 1.0

Incluye selección de ciudades, periodos, capas, opacidad, mapa claro/oscuro, medición aproximada, consulta, descarga GeoJSON, exportación PNG, indicadores demostrativos, gráfico y enlace configurable a Power BI. No incluye búsqueda de direcciones ni procesamiento espacial en servidor. Las ciudades sin capas se muestran como ubicaciones disponibles para futuras incorporaciones.
