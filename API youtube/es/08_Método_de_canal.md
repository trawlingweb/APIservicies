# API Youtube - Método GET /cannel

Permite la obtención de los datos del Canal emisor de un vídeo concreto.

El contenido devuelto són los datos del propia canal.


# Parámetros GET

Veamos la estructura de la consulta de ejemplo:


````
https://youtube.trawlingweb.com/channel/{ID_CHANNEL}/?token={APIKEY}
````

## Parámetros PATH

|      Elemento       | Descripción                                                 |
|:-------------------|:------------------------------------------------------------|
| protocolo | Puede ser tanto **http** como **https**                  |
| dominio | Dirección de la API youtube.trawlingweb.com |
| método | Método usado CHANNEL. Valor obligatorio |
| ID_CHANNEL | ID del canal a obtener sus datos. Valor obligatorio |
| parámetros | Parámetros de la consulta |


## Parámetros QUERY

| Parámetro | Descripción  | Default | Ejemplo    | 
|:----------|:-------------|:-------|:-----------|
| token | Código de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio |  ?token={APIKEY}


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API, éste devolverá los datos estructurados en función del método de obtención: 


## Datos de canal

| Campo | descripción | Tipo | Formato |
| ------- | ---------|:--------:|:---------:|
| id | ID que YouTube utiliza para identificar de forma exclusiva al canal. | Cadena | Cadena alfanumérica |

## Estadísticas de canal

| Campo | descripción | Tipo | Formato |
| ------- | ---------|:--------:|:---------:|
| viewCount | Cantidad de reproducciones que tiene el canal. | Número | Entero |
| commentCount | Número de comentarios del canal. | Número | Entero |
| hiddenSubscriberCount | Si se muestra o no el número de suscriptores para este canal. | Booleano | True/False |
| subscriberCount | Número de subscriptores del canal. | Número | Entero |
| videoCount | Número de vídeos que tiene el canal. | Número | Entero |


## Datos de petición

| Campo | Descripción | Tipo |
|:-----|:------|:--------:|
| requestLeft  | Total de consultas pendientes de la subscripción| Entero |



## Ejemplo de respuesta en formato json:


````json
"response" : {
  "data" : {
    "id" : "...",
    "statistics" : {
      "viewCount" : "...",
      "commentCount" : "...",
      "hiddenSubscriberCount" : "...",
      "subscriberCount" : "...",
      "videoCount" : "..."
    }
  },
  "requestLeft" : "..."
}
````