# API Youtube - Método GET /statistics

Permite la obtención de las últimas estadísticas diponibles del un vídeo concreto.

El contenido devuelto són als estadisticas del vídeo solicitado.


# Parámetros GET

Veamos la estructura de la consulta de ejemplo:


````
https://youtube.trawlingweb.com/statistics/{ID_VIDEO}/?token={APIKEY}
````

## Parámetros PATH

|      Elemento       | Descripción                                                 |
|:-------------------|:------------------------------------------------------------|
|        protocolo         | Puede ser tanto **http** como **https**                  |
| dominio | Dirección de la API youtube.trawlingweb.com |
| método | Método usado STATISTICS. Valor obligatorio |
| ID | ID del vídeo a obtener datos del método. Valor obligatorio |
| parámetros | Parámetros de la consulta |


## Parámetros QUERY

| Parámetro | Descripción  | Default | Ejemplo    | 
|:----------|:-------------|:-------|:-----------|
| token     | Código de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio |  ?token={APIKEY}


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API, éste devolverá los datos estructurados en función del método de obtención: 


## Estadísticas de noticia

| Campo | descripción | Tipo | Formato |
| ------- | ---------|:--------:|:---------:|
| id | ID que YouTube utiliza para identificar de forma exclusiva el vídeo. | Cadena | Cadena alfanumérica |
| viewCount | Cantidad de veces que se ha reproducido el vídeo. | Número | Entero |
| likeCont | Número de usuarios que indicaron que les gustó el vídeo, dándole una calificación positiva. | Número | Entero |
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
    "viewCount" : "...",
    "likeCont" : "...",
    "dislikeCount" : "...",
    "favoriteCount" : "...",
    "commentCount" : "..."
  }],
  "requestLeft" : "...",
}
````