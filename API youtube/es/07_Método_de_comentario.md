# API Youtube - Método GET /comments

Permite la obtención de los cometarios disponibles de un vídeo concreto.

El contenido devuelto són los comentarios del vídeo solicitado sin estadísticas ni datos descriptivos del mismo.


# Parámetros GET

Veamos la estructura de la consulta de ejemplo:


````
https://youtube.trawlingweb.com/comments/{ID_VIDEO}/?token={APIKEY}
````
## Parámetros PATH

| Elemento | Descripción |
|:---------|:------------|
| protocolo | Puede ser tanto **http** como **https** |
| dominio | Dirección de la API youtube.trawlingweb.com |
| método | Método usado COMMENTS. Valor obligatorio |
| ID_VIDEO | ID del vídeo a obtener datos del método. Valor obligatorio |
| parámetros | Parámetros de la consulta |


## Parámetros QUERY

| Parámetro | Descripción  | Default | Ejemplo | 
|:----------|:-------------|:-------|:-----------|
| token | Código de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio | ?token={APIKEY} |


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API, éste devolverá los datos estructurados en función del método de obtención: 


## Datos de comentarios de vídeo

| Campo | descripción | Tipo | Formato |
|:-------|---------|:--------:|:---------:|
| id | ID del comentario del vídeo. | Cadena | Cadena alfanumérica |
| totalReplyCount | Número de comentarios del vídeo. | Cadena | Cadena alfanumérica |
| isPublic | Esta configuración indica si el hilo, incluidos todos sus comentarios y respuestas de comentarios, es visible para todos los usuarios de YouTube. Los valores válidos para esta propiedad son: **true** o **false** | Cadena | Cadena alfanumérica | 
| authorDisplayName | El nombre para mostrar del usuario que publicó el comentario. | Cadena | Cadena alfanumérica |
| authorProfileImageUrl | La URL del avatar del usuario que publicó el comentario.  | Cadena | Cadena alfanumérica |
| authorChannelUrl | La URL del canal de YouTube del autor del comentario, si está disponible. | Cadena | Cadena alfanumérica |
| authorChannelId | La ID del canal de YouTube del autor del comentario, si está disponible. | Cadena | Cadena alfanumérica |
| textDisplay   | El texto del comentario. Tenga en cuenta que incluso el texto sin formato puede diferir del texto del comentario original. Por ejemplo, puede reemplazar enlaces de vídeo con títulos de vídeo.| Cadena | Cadena alfanumérica |
| textOriginal | El texto original sin procesar del comentario tal como se publicó inicialmente o se actualizó por última vez. El texto original solo se devuelve si es accesible para el usuario autenticado, lo cual solo se garantiza si el usuario es el autor del comentario. | Cadena | Cadena alfanumérica |
| viewerRating | La calificación que el espectador le ha dado a este comentario. Tenga en cuenta que esta propiedad no identifica actualmente las calificaciones de desagrado, aunque este comportamiento está sujeto a cambios. Mientras tanto, el valor de la propiedad es similar si el espectador ha calificado el comentario positivamente. El valor es ninguno en todos los demás casos, incluido que el usuario haya dado una calificación negativa al comentario o no haya calificado el comentario. Los valores válidos para esta propiedad son: **like** o **none** | Cadena | Cadena alfanumérica |
| likeCount     | Número de usuarios que indicaron que les gustó el comentario, dándole una calificación positiva. | Número | Entero |
| published | Fecha y hora en que se subió el comentario.  | Fecha | ISO 8601-UTC |
| updated | Fecha y hora en que se actualizó el comentario.  | Fecha | ISO 8601-UTC |
| canRate | Esta configuración indica si el espectador actual puede calificar el comentario. Los valores válidos para esta propiedad son: **true** o **false** | Cadena | Cadena alfanumérica | 
| replies | Lista de comentarios si estos existen | Número | Entero |
| replies.id | ID de la réplica del comentario del vídeo. | Cadena | Cadena alfanumérica |
| replies.totalReplyCount | Número de réplicas de comentarios del vídeo. | Cadena | Cadena alfanumérica |
| replies.isPublic | Esta configuración indica si el hilo, incluidos todos sus comentarios y réplicas de comentarios, es visible para todos los usuarios de YouTube. Los valores válidos para esta propiedad son: **true** o **false** | Cadena | Cadena alfanumérica | 
| replies.authorDisplayName | El nombre para mostrar del usuario que publicó la réplica del comentario. | Cadena | Cadena alfanumérica |
| replies.authorProfileImageUrl | La URL del avatar del usuario que publicó la réplica del comentario.  | Cadena | Cadena alfanumérica |
| replies.authorChannelUrl | La URL del canal de YouTube del autor de la réplica del comentario, si está disponible. | Cadena | Cadena alfanumérica |
| replies.authorChannelId | La ID del canal de YouTube del autor la réplica del comentario, si está disponible. | Cadena | Cadena alfanumérica |
| replies.textDisplay | El texto la réplica del comentario. Tenga en cuenta que incluso el texto sin formato puede diferir del texto del comentario original. Por ejemplo, puede reemplazar enlaces de vídeo con títulos de vídeo.| Cadena | Cadena alfanumérica |
| replies.textOriginal | El texto original sin procesar la réplica del comentario tal como se publicó inicialmente o se actualizó por última vez. El texto original solo se devuelve si es accesible para el usuario autenticado, lo cual solo se garantiza si el usuario es el autor del comentario. | Cadena | Cadena alfanumérica |
| replies.viewerRating | La calificación que el espectador le ha dado a esta réplica del comentario. Tenga en cuenta que esta propiedad no identifica actualmente las calificaciones de desagrado, aunque este comportamiento está sujeto a cambios. Mientras tanto, el valor de la propiedad es similar si el espectador ha calificado el comentario positivamente. El valor es ninguno en todos los demás casos, incluido que el usuario haya dado una calificación negativa al comentario o no haya calificado el comentario. Los valores válidos para esta propiedad son: **like** o **none** | Cadena | Cadena alfanumérica |
| replies.likeCount | Número de usuarios que indicaron que les gustó la réplica del comentario, dándole una calificación positiva. | Número | Entero |
| replies.published | Fecha y hora en que se subió la réplica del comentario.  | Fecha | ISO 8601-UTC |
| replies.updated | Fecha y hora en que se actualizó la réplica del comentario.  | Fecha | ISO 8601-UTC |
| replies.canRate | Esta configuración indica si el espectador actual puede calificar la réplica del comentario. Los valores válidos para esta propiedad son: **true** o **false** | Cadena | Cadena alfanumérica | 
| replies.parentId | La ID única del comentario padre. Esta propiedad solo se establece si el comentario se envió como réplica a otro comentario. | Booleano | 0 o 1 | 



## Datos de petición

| Campo | Descripción | Tipo |
|:-----|:------|:--------:|
| requestLeft  | Total de consultas pendientes de la subscripción| Entero |
| totalResults | Total aproximado de resultados encontrados por la consulta | Entero |
| pageResults  | Número de vídeos listados | Entero |
| next | URL para continuar con la paginación y así obtener todos los resultados | Cadena |


## Ejemplo de respuesta en formato json:


````json
"response" : {
  "data" : {
    "id" : "...",
    "totalReplyCount" : "...",
    "isPublic" : "...",
    "authorDisplayName" : "...",
    "authorProfileImageUrl" : "...",
    "authorChannelUrl" : "...",
    "authorChannelId" : "...",
    "textDisplay" : "...",
    "textOriginal" : "...",
    "viewerRating" : "...",
    "likeCount" : ["...","...","..."],
    "published" : "...",
    "updated" : "...",
    "canRate" : "...",
    "replies" : [{
      "replies.id" : "...",
      "replies.totalReplyCount" : "...",
      "replies.isPublic " : "...",
      "replies.authorDisplayName" : "...",
      "replies.authorProfileImageUrl" : "...",
      "replies.authorChannelUrl" : "...",
      "replies.authorChannelId" : "...",
      "replies.textDisplay" : "...",
      "replies.textOriginal" : "...",
      "replies.viewerRating" : "...",
      "replies.published" : "...",
      "replies.updated" : "...",
      "replies.canRate" : "...",
      "replies.parentId" : "..."
    }]
  },
  "requestLeft" : "...",
  "totalResults" : "...",
  "restResults" : "...",
  "next" : "..."
}
````