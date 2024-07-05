# API Twitter - Método GET /posts

Permite obtener resultado capturados de cada Worker configurado de Twitter.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

```
https://twitter.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## Parámetros PATH

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API twitter.trawlingweb.com   |
| método    | posts                                         |
| workerid  | WORKERID de acceso al sistema de TrawlingWeb. |

## Parámetros QUERY

| Parámetro | Descripción                                                                  | Default                                                 | Ejemplo            |
| :-------- | :--------------------------------------------------------------------------- | :------------------------------------------------------ | :----------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb.                      | Valor obligatorio                                       | ?token={APIKEY}    |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000  |
| tsi       | Se trata del delimitador temporal final. Formato Unix Time en milisegundos   | Delimita con la fecha de petición                       | &tsi=1524818189854 |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Twitter éste devolverá una respuesta estructurada de la siguiente forma:

## Datos de la publicación

| Campo                  | Descripción                                                                                                                                                                       | Buscable | Ordenable |  Tipo   |           Formato           |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------: | :-------: | :-----: | :-------------------------: |
| id                     | Código de indentificación asignado por Trawlingweb a cada publicación rastreada                                                                                                   |    No    |    No     | Cadena  |                             |
| hash                   | Código de indentificación en base al texto                                                                                                                                        |    No    |    No     | Cadena  |                             |
| published              | Fecha publicado el post                                                                                                                                                           |    No    |    No     |  Fecha  |        ISO 8601-UTC         |
| crawled                | Fecha de captura                                                                                                                                                                  |    No    |    Si     | Entero  | UNIX Timestamp milisegundos |
| updated                | Fecha de actualitzación                                                                                                                                                           |    No    |    Si     | Entero  | UNIX Timestamp milisegundos |
| post_id                | Id del post                                                                                                                                                                       |    No    |    No     | Cadena  |                             |
| url                    | Url de la publicación                                                                                                                                                             |    No    |    No     | Cadena  |                             |
| text                   | Texto descrito de la publicación                                                                                                                                                  |    No    |    No     | Cadena  |                             |
| lang                   | Cuando está presente, indica un identificador de idioma BCP 47 correspondiente al idioma detectado por la máquina del texto del Tweet, o und si no se pudo detectar ningún idioma |    No    |    No     | String  |                             |
| retweet_count          | Número de veces que este Tweet ha sido retwiteado.                                                                                                                                |    No    |    No     | Integer |                             |
| reply_count            | Número de veces que este Tweet ha sido respondido                                                                                                                                 |    No    |    No     | Integer |                             |
| favorite_count         | Indica aproximadamente cuántas veces ha gustado a los usuarios de Twitter este Tweet                                                                                              |    No    |    No     | Integer |                             |
| reproductions_count    | Número de veces que este Tweet ha sido reproducido                                                                                                                                |    No    |    No     | Integer |                             |
| user_name              | Nombre de usuario                                                                                                                                                                 |    No    |    No     | Cadena  |                             |
| user_screen_name       | Nombre de usuario mostrado                                                                                                                                                        |    No    |    No     | Cadena  |                             |
| user_url               | Url del usuario                                                                                                                                                                   |    No    |    No     | Cadena  |                             |
| user_profile_image_url | Una URL basada en HTTP que apunta a la imagen de perfil del usuario                                                                                                               |    No    |    No     | Cadena  |                             |
| entities_url           | Enlaces mencionados                                                                                                                                                               |    no    |    no     | Cadena  |                             |
| hashtags               | Hashtags referenciados en el texto                                                                                                                                                |    No    |    No     | Cadena  |                             |
| user_mentions          | Nombres referenciados en el texto                                                                                                                                                 |    No    |    No     | Cadena  |                             |
| time_distance          | Horas transcurridas entre la fecha de publicación y la de captura                                                                                                                 |    No    |    No     | Decimal |                             |
| reply                  | Indica si es una respuesta a un Tweet                                                                                                                                             |    No    |    No     | Boleano |                             |

## Ejemplo de respuesta en formato json:

```json
"response" : {
    "data" : [{
        "id": "...",
        "hash": "...",
        "published" : "...",
        "crawled" : "...",
        "updated" : "...",
        "post_id" : "...",
        "url" : "...",
        "text" : "...",
        "lang" : "...",
        "retweet_count" : "...",
        "reply_count" : "...",
        "favorite_count" : "...",
        "reproductions_count" : "...",
        "created_at" : "...",
        "user_name" : "...",
        "user_screen_name" : "...",
        "user_url" : "...",
        "user_profile_image_url" : "...",
        "entities_url" : "...",
        "hashtags" : "...",
        "user_mentions" : "...",
        "time_distance" : "...",
        "reply" : "...",
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Twitter - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado y su id de Worker.
Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/workers).

## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de r00 elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
next	"http://twitter.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
```

## Paginación

Al realizar peticiones a los métodos POST estos devuelven un máximo de 100 resultados. Se habilita una url de next para continuar con la obtención si estos superan dicha cantidad.
