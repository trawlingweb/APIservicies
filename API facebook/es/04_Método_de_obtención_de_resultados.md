# API Facebook - Método GET /posts

Permite obtener resultado capturados de cada Worker configurado de Facebook.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

La llamada a la API se construye a partir de la estructura básica:

```
https://facebook.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## Parámetros PATH

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API Facebook.trawlingweb.com   |
| método    | posts                                         |
| workerid  | Identificador que permite acceder a un worker específico y recuperar los resultados generados por las palabras clave configuradas en él. Funciona como una biblioteca o lista de palabras clave, permitiendo obtener resultados relevantes basados en dichas palabras clave. |


## Parámetros QUERY

| Parámetro | Descripción                                                                  | Default                                                 | Ejemplo            |
| :-------- | :--------------------------------------------------------------------------- | :------------------------------------------------------ | :----------------- |
| token     | APIKEY para validar y acceder al sistema de TrawlingWeb. Cada usuario tiene su propia APIKEY individual e intransferible, vinculada a sus servicios y características.           | Valor obligatorio                                       | ?token={APIKEY}    |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000  |
| tsi       | Se trata del delimitador temporal final. Formato Unix Time en milisegundos   | Delimita con la fecha de petición                       | &tsi=1524818189854 |


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Facebook éste devolverá una respuesta estructurada de la siguiente forma:

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
| favorite_count         | Indica aproximadamente cuántas veces ha gustado a los usuarios de Facebook este Tweet                                                                                              |    No    |    No     | Integer |                             |
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
## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
next	"http://facebook.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
- [Correo SAT](mailto:support@trawlingweb.com)
- [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
- [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
- [Correo Ventas](mailto:sales@trawlingweb.com)
s
