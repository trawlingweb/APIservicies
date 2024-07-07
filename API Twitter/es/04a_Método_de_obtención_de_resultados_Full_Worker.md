# API Twitter - Método GET /posts_full Worker

Permite obtener resultado capturados de cada Worker configurado de Twitter.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

```
https://twitter.trawlingweb.com/posts_full/{WORKERID}?token={APIKEY}
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

| Campo                   | Descripción                                                                                                                                                                       | Buscable | Ordenable |  Tipo   |           Formato           |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------: | :-------: | :-----: | :-------------------------: |
| id                      | Código de indentificación asignado por Trawlingweb a cada publicación rastreada                                                                                                   |    No    |    No     | Cadena  |                             |
| hash                    | Código de indentificación en base al texto                                                                                                                                        |    No    |    No     | Cadena  |                             |
| published               | Fecha publicado el post                                                                                                                                                           |    No    |    No     |  Fecha  |        ISO 8601-UTC         |
| crawled                 | Fecha de captura                                                                                                                                                                  |    No    |    Si     | Entero  | UNIX Timestamp milisegundos |
| updated                 | Fecha de actualitzación                                                                                                                                                           |    No    |    Si     | Entero  | UNIX Timestamp milisegundos |
| post_id                 | Id del post                                                                                                                                                                       |    No    |    No     | Cadena  |                             |
| url                     | Url de la publicación                                                                                                                                                             |    No    |    No     | Cadena  |                             |
| text                    | Texto descrito de la publicación                                                                                                                                                  |    No    |    No     | Cadena  |                             |
| lang                    | Cuando está presente, indica un identificador de idioma BCP 47 correspondiente al idioma detectado por la máquina del texto del Tweet, o und si no se pudo detectar ningún idioma |    No    |    No     | Cadena  |                             |
| retweet_count           | Número de veces que este Tweet ha sido retwiteado.                                                                                                                                |    No    |    No     | Integer |                             |
| reply_count             | Número de veces que este Tweet ha sido respondido                                                                                                                                 |    No    |    No     | Integer |                             |
| favorite_count          | Indica aproximadamente cuántas veces ha gustado a los usuarios de Twitter este Tweet                                                                                              |    No    |    No     | Integer |                             |
| reproductions_count     | Número de veces que este Tweet ha sido reproducido                                                                                                                                |    No    |    No     | Integer |                             |
| entities_url            | Enlaces mencionados                                                                                                                                                               |    no    |    no     | Cadena  |                             |
| url_image               | Enlaces de imagenes                                                                                                                                                               |    no    |    no     | Cadena  |                             |
| hashtags                | Hashtags referenciados en el texto                                                                                                                                                |    No    |    No     | Cadena  |                             |
| user_mentions           | Nombres referenciados en el texto                                                                                                                                                 |    No    |    No     | Cadena  |                             |
| time_distance           | Horas transcurridas entre la fecha de publicación y la de captura                                                                                                                 |    No    |    No     | Decimal |                             |
| reply                   | Indica si es una respuesta a un Tweet                                                                                                                                             |    No    |    No     | Boleano |                             |
| user_id                 | Código de indentificación de usuario                                                                                                                                              |    No    |    No     | Entero  |                             |
| user_name               | Nombre de usuario                                                                                                                                                                 |    No    |    No     | Cadena  |                             |
| user_screen_name        | Nombre de usuario mostrado                                                                                                                                                        |    No    |    No     | Cadena  |                             |
| user_creation_date      | Fecha de creación del usuario                                                                                                                                                     |    No    |    No     |  Fecha  |        ISO 8601-UTC         |
| user_url                | Url del usuario                                                                                                                                                                   |    No    |    No     | Cadena  |                             |
| user_profile_image_url  | Una URL basada en HTTP que apunta al abatar del perfil del usuario                                                                                                                |    No    |    No     | Cadena  |                             |
| user_profile_banner_url | Una URL basada en HTTP que apunta al banner del perfil del usuario                                                                                                                |    No    |    No     | Cadena  |                             |
| user_description        | Texto descrito del usuario                                                                                                                                                        |    No    |    No     | Cadena  |                             |
| user_external_url       | Url del la descripción del usuario                                                                                                                                                |    No    |    No     | Cadena  |                             |
| user_location           | Ubicación que el usuario específica                                                                                                                                               |    No    |    No     | Cadena  |                             |
| user_follower_count     | Número de seguidores del usuario                                                                                                                                                  |    No    |    No     | Integer |                             |
| user_following_count    | Número de seguidos del usuario                                                                                                                                                    |    No    |    No     | Integer |                             |
| user_favourites_count   | Número de favoritos del usuario                                                                                                                                                   |    No    |    No     | Integer |                             |
| user_is_private         | Usuario privado                                                                                                                                                                   |    No    |    No     | Boleano |                             |
| user_is_verified        | Usuario verificado                                                                                                                                                                |    No    |    No     | Boleano |                             |
| user_is_blue_verified   | Usuario verificado como Blue                                                                                                                                                      |    No    |    No     | Boleano |                             |
| user_number_of_tweets   | Número de Tweets realiados por el usario                                                                                                                                          |    No    |    No     | Integer |                             |

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
        "entities_url" : "...",
        "url_image" : "...",
        "hashtags" : "...",
        "user_mentions" : "...",
        "time_distance" : "...",
        "reply" : "...",
        "user_name" : "...",
        "user_screen_name" : "...",
        "user_creation_date" : "...",
        "user_url" : "...",
        "user_profile_image_url" : "...",
        "user_profile_banner_url" : "...",
        "user_description" : "...",
        "user_external_url" : "...",
        "user_location" : "...",
        "user_follower_count" : "...",
        "user_following_count" : "...",
        "user_favourites_count" : "...",
        "user_is_private" : "...",
        "user_is_verified" : "...",
        "user_is_blue_verified" : "...",
        "user_number_of_tweets" : "...",
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Twitter - Mejores prácticas

## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de 500 elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
next	"http://twitter.trawlingweb.com/posts_full/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
```

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
- [Correo SAT](mailto:support@trawlingweb.com)
- [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
- [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
- [Correo Ventas](mailto:sales@trawlingweb.com)

