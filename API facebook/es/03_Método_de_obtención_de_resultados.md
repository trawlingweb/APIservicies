# API Facebook - Método GET /posts

Permite obtener resultado capturados de cada Worker configurado de Facebook.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

````
https://facebook.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
````

## Parámetros PATH

| Elemento | Descripción |
|:---------|:------------|
| protocolo | Puede ser tanto **http** como **https** |
| dominio | Dirección de la API facebook.trawlingweb.com |
| método | posts |
| workerid | WORKERID de acceso al sistema de TrawlingWeb. 

## Parámetros QUERY

| Parámetro | Descripción | Default | Ejemplo | 
|:----------|:-------------|:-------|:-----------|
| token | APIKEY de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio | ?token={APIKEY}
| ts | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000 |
| tsi | Se trata del delimitador temporal final. Formato Unix Time en milisegundos | Delimita con la fecha de petición | &tsi=1524818189854 |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Facebook éste devolverá una respuesta estructurada de la siguiente forma: 

## Datos de la publicación

| Campo | Descripción | Buscable | Ordenable | Tipo | Formato |
|-------------|--------|:--------:|:---------:|:------:|:-------:|
| id | Código de indentificación asignado por Trawlingweb a cada publicación rastreada.| No | No | Cadena |
| type | Tipo de publicación ( posts, photos, photo, notes, permalink, videos ) | No | No | Cadena |
| url | Url de la publicación | No | No | Cadena |
| likes_num | Cantidad de likes | No | No | Entero |
| comments_num | Cantidad de comentarios | No | No | Entero |
| shared_num | Cantidad de comparticiones | No | No | Entero |
| text | Texto descrito de la publicación | No | No| Cadena |
| published | Fecha publicado el post | No | No | Fecha | ISO 8601-UTC |
| language |  Idioma de la publicación (Disponible cuando el idioma es detectado con el texto disponible)| Si | No | Cadena | ISO 639-1 |
| language\_detection\_precision | Precisión de la detección (Disponible cuando el idioma es detectado con el texto disponible) |  No | No | Entero |
| crawled | Id crawled | No | Si | Entero | UNIX Timestamp milisegundos |

## Datos del usuario

| Campo | Descripción | Buscable | Ordenable | Tipo | Formato |
|-------------|--------|:--------:|:---------:|:------:|:-------:|
| user_name  | Nombre de usuario |  No | No | Cadena |
| user_screen_name | Nombre de usuario mostrado | No | No | Cadena | 
| user_url | Url de usuario, canal o página | No | No | Cadena |

## Datos de petición

| Campo | Descripción | Tipo |
|:-----|:------|:--------:|
| requestLeft | Total de consultas pendientes de la subscripción| Entero |
| totalResults | Total de resultados encontrados por la consulta | Entero |
| next | URL para continuar con la paginación y así obtener todos los resultados | Cadena |

## Ejemplo de respuesta en formato json:

````json
"response" : {
    "data" : [{
        "id" : "...",
        "user_name" : "...",
        "user_screen_name" : "...",
        "user_url" : "...",
        "type" : "...",
        "url" : "...",
        "text" : "...",
        "likes_num" : "...",
        "comments_num" : "...",
        "shared_num" : "...",
        "published" : "...",
        "crawled" : "...",
        "language": "es",
        "language_detection_precision": ".."
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
````

# API Facebook - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado y su id de Worker.
Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/workers).

## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de 100 elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

````
requestLeft	9999999
totalResults	295404987
next	"http://facebook.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
````

## Paginación

Al realizar peticiones a los métodos POST estos devuelven un máximo de 100 resultados. Se habilita una url de next para continuar con la obtención si estos superan dicha cantidad.
