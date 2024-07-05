# API Youtube - Método GET /video

Permite la obtención de los últimos datos descriptivos de un vídeo concreto.

El contenido devuelto són los datos descriptivos del vídeo solicitado sin estadísticas ni comentarios del mismo.


# Parámetros GET

Veamos la estructura de la consulta de ejemplo:


````
https://youtube.trawlingweb.com/video/{ID_VIDEO}/?token={APIKEY}
````

## Parámetros PATH

|      Elemento       | Descripción                                                 |
|:-------------------|:------------------------------------------------------------|
|        protocolo         | Puede ser tanto **http** como **https**                  |
| dominio | Dirección de la API youtube.trawlingweb.com |
| método | Método usado VIDEO. Valor obligatorio |
| ID | ID del vídeo a obtener datos del método. Valor obligatorio |
| parámetros | Parámetros de la consulta |


## Parámetros QUERY

| Parámetro | Descripción  | Default | Ejemplo    | 
|:----------|:-------------|:-------|:-----------|
| token     | Código de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio |  ?token={APIKEY}


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API, éste devolverá los datos estructurados en función del método de obtención: 


## Datos de vídeo

| Campo | descripción | Tipo | Formato |
| ------- | ---------|:--------:|:---------:|
| id | ID que YouTube utiliza para identificar de forma exclusiva el vídeo. | Cadena | Cadena alfanumérica |
| url | Url de visualización. | Cadena | Cadena alfanumérica |
| urlShort | Url de visualización acortada | Cadena | Cadena alfanumérica | 
| urlEmbed | Url de incrustación. | Cadena | Cadena alfanumérica |
| published | Fecha y hora en que se subió el vídeo.  | Fecha | ISO 8601-UTC |
| channelId | ID que YouTube utiliza para identificar de forma exclusiva el canal al que se subió el vídeo. | Cadena | Cadena alfanumérica |
| channelTitle | Título del vídeo. | Cadena | Cadena alfanumérica |
| description | Descripción del vídeo.| Cadena| Cadena alfanumérica |
| thumbnails | Mapa de imágenes en miniatura asociadas con el vídeo. Para cada objeto en el mapa, la clave es el nombre de la imagen en miniatura, y el valor es un objeto que contiene otra información sobre la viñeta. Los valores de clave válidos son: **default:** Imagen en miniatura predeterminada. La viñeta predeterminada para un vídeo, o de un recurso que hace referencia a un vídeo, como un elemento de una lista de reproducción o el resultado de una búsqueda, es de 120 pixeles de ancho y 90 píxeles de alto. La viñeta predeterminada para un canal es de 88 píxeles de ancho y 88 píxeles de alto. **medium:** Versión de mayor resolución de la imagen en miniatura. Para un vídeo (o un recurso que hace referencia a un vídeo), esta imagen es de 320 píxeles de ancho y 180 píxeles de alto. Para un canal, esta imagen es de 240 píxeles de ancho y 240 píxeles de alto. **high:** Versión de alta resolución de la imagen en miniatura. Para un vídeo (o un recurso que hace referencia a un vídeo), esta imagen es de 480 píxeles de ancho y 360 píxeles de alto. Para un canal, esta imagen es de 800 píxeles de ancho y 800 píxeles de alto. | Lista | Cadena alfanumérica |
| tags | Lista de etiquetas de palabras clave asociadas con el vídeo. Las etiquetas pueden contener espacios. Este campo es visible solo para quien sube el vídeo. | Lista | Cadena alfanumérica |
| categoryId | Categoría de vídeo de YouTube asociada con el vídeo. | Número | Entero |
| liveBroadcastContent | Indica si el contenido es en directo. Los valores pueden ser  **live** o **none** | Cadena | Cadean alfanumérica | 
| viewCount | Cantidad de veces que se ha reproducido el vídeo. | Número | Entero |
| likeCount | Número de usuarios que indicaron que les gustó el vídeo, dándole una calificación positiva. | Número | Entero |
| dislikeCount | Número de usuarios que indicaron que no les gustó el vídeo, dándole una calificación negativa. | Número | Entero |
| favoriteCount | Número de usuarios que actualmente tienen marcado el vídeo como vídeo favorito. | Número | Entero |
| commentCount | Número de comentarios del vídeo. | Número | Entero |


## Datos de petición

| Campo | Descripción | Tipo |
|:-----|:------|:--------:|
| requestLeft  | Total de consultas pendientes de la subscripción| Entero |


## Ejemplo de respuesta en formato json:


````json
"response" : {
  "data" : [{
    "id" : "...",
    "url" : "...",
    "urlShort" : "...",
    "urlEmbed" : "...",
    "published" : "...",
    "channelId" : "...",
    "channelTitle" : "...",
    "description" : "...",
    "thumbnails" : {
      "defaul":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "medium":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "high":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "standard":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "maxres":{
          "url":"...",
          "width":"...",
          "height":"..."
      }
    },
    "tags" : ["...","...","..."],
    "categoryId" : "...",
    "liveBroadcastContent" : "...",
    "viewCount" : "...",
    "likeCount" : "...",
    "dislikeCount" : "...",
    "favoriteCount" : "...",
    "commentCount" : "..."
  }],
  "requestLeft" : "...",
}
````