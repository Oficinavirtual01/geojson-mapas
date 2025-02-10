
# Jurisdicciones de Comisarías - GeoJSON

Este archivo contiene las jurisdicciones de las comisarías en formato GeoJSON.  
Cada jurisdicción tiene los siguientes atributos:  

- **id**: Identificador único de la jurisdicción.  
- **name**: Nombre de la comisaría.  
- **color**: Código de color en formato HEX para la visualización en mapas.  
- **tooltip**: Texto que se mostrará al pasar el mouse sobre la jurisdicción en el mapa.  

## Edición del Archivo  
Puedes editar este archivo directamente desde GitHub para modificar colores o nombres sin necesidad de cambiar el código en Google Apps Script.  

Ejemplo de una jurisdicción en el archivo JSON:  
```json
{
    "type": "Feature",
    "properties": {
        "id": 1,
        "name": "Comisaría 1",
        "color": "#FF5733",
        "tooltip": "Comisaría 1"
    },
    "geometry": {
        "type": "Polygon",
        "coordinates": [...]
    }
}
```

## Integración con Google Maps API  
Para mostrar tooltips en Google Maps API, usa el siguiente código en tu script de Apps Script:

```javascript
map.data.addListener('mouseover', function(event) {
    let tooltip = event.feature.getProperty('tooltip');
    let infoWindow = new google.maps.InfoWindow({
        content: tooltip,
        position: event.latLng
    });
    infoWindow.open(map);
});
```

Cualquier modificación en este archivo en GitHub se reflejará automáticamente en la API de Google Maps cuando se cargue el mapa.  
