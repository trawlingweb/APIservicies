# API TikTok - Método GET /posts

Permite obtener resultados procesados de cada Worker configurado de TikTok.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

```
https://tiktok.trawlingweb.com/posts/?cursor=XXX&token=YYY
```

## Parámetros PATH

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API tiktok.trawlingweb.com |
| método    | posts                                         |
| workerid  | WORKERID de acceso al sistema de TrawlingWeb. |

## Parámetros QUERY

| Parámetro | Descripción                                                                  | Default                                                 | Ejemplo            |
| :-------- | :--------------------------------------------------------------------------- | :------------------------------------------------------ | :----------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb.                      | Valor obligatorio                                       | ?token={APIKEY}    |
| country_pref| Preferencia de país del cliente (ISO 3166-1 alpha-2, ej: `es`). **Obligatorio para contratos FeedScale Pay-per-Use**. Su omisión penaliza multiplicando x2.5 el coste de la request y conlleva riesgo de bloqueo de acceso. | Obligatorio (Pay-per-Use)                               | &country_pref=es              |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000  |
| tsi       | Se trata del delimitador temporal final. Formato Unix Time en milisegundos   | Delimita con la fecha de petición                       | &tsi=1524818189854 |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición a la API de TikTok, esta devolverá una respuesta estructurada de la siguiente forma:

> La columna **Buscable** indica si el campo puede usarse dentro del parámetro `q=` con sintaxis Lucene. Los campos marcados como buscables aceptan tanto la búsqueda por keyword (sobre el conjunto de campos de texto por defecto) como el filtrado por atributo (`campo:valor`).

## Datos de la publicación

| Campo     | Descripción                                                                 | Buscable | Ordenable |  Tipo  |           Formato           |
| --------- | --------------------------------------------------------------------------- | :------: | :-------: | :----: | :-------------------------: |
| id        | Código de identificación asignado por Trawlingweb a cada publicación rastreada |    No    |    No     | Cadena |                             |
| post_id   | ID de la publicación                                                        |    No    |    No     | Cadena |                             |
| type      | Tipo de publicación (foto o video)                                          |    No    |    No     | Cadena |                             |
| url       | URL de la publicación                                                       |    No    |    No     | Cadena |                             |
| media_url | URL del contenido multimedia                                                |    No    |    No     | Cadena |                             |
| likes     | Cantidad de "me gusta"                                                      |    No    |    No     | Entero |                             |
| text      | Texto descriptivo de la publicación                                         |    Sí    |    No     | Cadena |                             |
| music_title | Título de la música/audio asociado al post                                |    Sí    |    No     | Cadena |                             |
| region    | País asociado a la publicación (ISO 3166-1 alpha-2, minúsculas)             |    Sí    |    No     | Cadena | `mx`, `es`, `ar`, `co`, `us`… |
| language  | Idioma detectado del contenido (ISO 639-1, minúsculas; `un` = indefinido)   |    Sí    |    No     | Cadena | `es`, `en`, `pt`, `un`…      |
| published | Fecha de publicación del post                                               |    No    |    No     |  Fecha |        ISO 8601-UTC         |
| crawled   | Fecha y hora en que se indexó la publicación                               |    No    |    Sí     | Entero | Timestamp UNIX en milisegundos |

## Datos del usuario

| Campo             | Descripción                                                          | Buscable | Ordenable |  Tipo  | Formato |
| ----------------- | -------------------------------------------------------------------- | :------: | :-------: | :----: | :-----: |
| user_name         | Nombre de usuario                                                    |    Sí    |    No     | Cadena |         |
| user_screen_name  | Nombre de usuario mostrado (handle)                                  |    Sí    |    No     | Cadena |         |
| user_id_name      | Identificador interno del usuario                                    |    Sí    |    No     | Cadena |         |
| user_signature    | Bio/descripción del perfil del creador                               |    Sí    |    No     | Cadena |         |
| user_region       | País declarado en el perfil del creador (ISO 3166-1, minúsculas)     |    Sí    |    No     | Cadena | `mx`, `es`, `ar`… |
| user_language     | Idioma del perfil del creador (ISO 639-1, minúsculas)                |    Sí    |    No     | Cadena | `es`, `en`, `un`… |
| user_publications | Número de publicaciones                                              |    No    |    No     | Entero |         |
| user_followers    | Número de seguidores                                                 |    No    |    No     | Entero |         |
| user_followed     | Número de usuarios seguidos                                          |    No    |    No     | Entero |         |

## Datos de los comentarios

| Campo    | Descripción  | Buscable | Ordenable |  Tipo  | Formato |
| -------- | ------------ | :------: | :-------: | :----: | :-----: |
| comments | Comentarios  |    No    |    No     | Cadena |         |

> **Aviso sobre `region` / `language` / `user_region` / `user_language`:** estos valores provienen directamente de TikTok — los entregamos tal cual los recibimos, sin recalcularlos ni validarlos. TikTok no siempre etiqueta con precisión (posts marcados `region:uy` que en realidad son `mx`, contenido en español etiquetado como `language:en` o `language:un` por errores del detector con textos cortos, hashtags o emojis, etc.). Úsalos como filtro para acotar volumen y reducir ruido, pero no como verdad absoluta; si necesitas cobertura exhaustiva de un mercado combina con keywords locales y varias regiones a la vez.

## Datos de la petición

| Campo        | Descripción                                                             |  Tipo  |
| :----------- | :---------------------------------------------------------------------- | :----: |
| requestLeft  | Total de consultas pendientes de la suscripción                         | Entero |
| totalResults | Total de resultados encontrados por la consulta                         | Entero |
| next         | URL para continuar con la paginación y así obtener todos los resultados | Cadena |

## Ejemplo de respuesta en formato JSON:

```json
{
  "data": [
    {
      "id": "...",
      "post_id": "...",
      "type": "...",
      "url": "...",
      "media_url": "...",
      "text": "...",
      "region": "mx",
      "language": "es",
      "music_title": "...",
      "likes": 125,
      "user_name": "...",
      "user_screen_name": "...",
      "user_id_name": "...",
      "user_signature": "...",
      "user_region": "mx",
      "user_language": "es",
      "user_publications": 239,
      "user_followers": 6762,
      "user_followed": 1792,
      "comments": null,
      "published": "2024-08-03T11:00:04.000Z",
      "crawled": 1722682829465
    }
  ],
  "totalResults": "...",
  "restResults": "...",
  "next": "..."
}
```

# API TikTok - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado y su id de Worker.
Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/workers).

## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de 100 elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
next	"http://tiktok.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
```

## Paginación

Al realizar peticiones a los métodos POST estos devuelven un máximo de 100 resultados. Se habilita una url de next para continuar con la obtención si estos superan dicha cantidad.

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://github.com/trawlingweb/APIservicies/tree/main/API%20TikTok)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)
s
