# API Instagram - Método GET /posts

Permite obtener resultado capturados de cada Worker configurado de Instagram.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

```
https://instagram.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## Parámetros PATH

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API instagram.trawlingweb.com |
| método    | posts                                         |
| workerid  | WORKERID de acceso al sistema de TrawlingWeb. |

## Parámetros QUERY

| Parámetro | Descripción                                                                  | Default                                                 | Ejemplo            |
| :-------- | :--------------------------------------------------------------------------- | :------------------------------------------------------ | :----------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb.                      | Valor obligatorio                                       | ?token={APIKEY}    |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000  |
| tsi       | Se trata del delimitador temporal final. Formato Unix Time en milisegundos   | Delimita con la fecha de petición                       | &tsi=1524818189854 |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Instagram éste devolverá una respuesta estructurada de la siguiente forma:

## Datos de la publicación

| Campo     | Descripción                                                              | Buscable | Ordenable |  Tipo  |           Formato           |
| --------- | ------------------------------------------------------------------------ | :------: | :-------: | :----: | :-------------------------: |
| id        | Identification code assigned by Trawlingweb to each tracked publication. |    No    |    No     | String |                             |
| post_id   | Id del post                                                              |    No    |    No     | Cadena |                             |
| type      | Tipo de publicación( photo o video )                                     |    No    |    No     | Cadena |                             |
| url       | Url de la publicación                                                    |    No    |    No     | Cadena |                             |
| media_url | Dirección web media content                                              |    No    |    No     | Cadena |                             |
| likes     | Cantidad de likes                                                        |    No    |    No     | Entero |                             |
| text      | Texto descrito de la publicación                                         |    No    |    No     | Cadena |                             |
| published | Fecha publicado el post                                                  |    No    |    No     | Fecha  |        ISO 8601-UTC         |
| crawled   | Id crawled                                                               |    No    |    Si     | Entero | UNIX Timestamp milisegundos |

## Datos del usuario

| Campo             | Descripción                 | Buscable | Ordenable |  Tipo  | Formato |
| ----------------- | --------------------------- | :------: | :-------: | :----: | :-----: |
| user_name         | Nombre de usuario           |    No    |    No     | Cadena |         |
| user_screen_name  | Nombre de usuario           |    No    |    No     | Cadena |         |
| user_publications | Numero de publicaciones     |    No    |    No     | Entero |         |
| user_followers    | Numero de seguidores        |    No    |    No     | Entero |         |
| user_followed     | Numero de usuarios seguidos |    No    |    No     | Entero |         |

## Datos de comments

| Campo    | Descripción | Buscable | Ordenable |  Tipo  | Formato |
| -------- | ----------- | :------: | :-------: | :----: | :-----: |
| comments | comentarios |    No    |    No     | Cadena |         |

## Datos de petición

| Campo        | Descripción                                                             |  Tipo  |
| :----------- | :---------------------------------------------------------------------- | :----: |
| requestLeft  | Total de consultas pendientes de la subscripción                        | Entero |
| totalResults | Total de resultados encontrados por la consulta                         | Entero |
| next         | URL para continuar con la paginación y así obtener todos los resultados | Cadena |

## Ejemplo de respuesta en formato json:

```json
"response" : {
    "data" : [{
        "id": "...",
        "post_id": "...",
        "type": "...",
        "url": "...",
        "media_url": "...",
        "user_name": "...",
        "likes": "...",
        "text": "...",
        "comments": "...",
        "published": "...",
        "crawled": "...",
        "user_screen_name": "...",
        "user_publications": "...",
        "user_followers": "...",
        "user_followed": "..."
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Instagram - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado y su id de Worker.
Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/workers).

## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de 100 elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
next	"http://instagram.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
```

## Paginación

Al realizar peticiones a los métodos POST estos devuelven un máximo de 100 resultados. Se habilita una url de next para continuar con la obtención si estos superan dicha cantidad.

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)
s
