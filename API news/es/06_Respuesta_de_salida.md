# API NEWS & BLOGS - Respuesta de salida

Una vez lanzada una petición al API, éste devolverá una respuesta con dos tipos de datos diferenciados:

## Datos de noticia

| Campo           | descripción                                                                                  | Buscable | Ordenable |          Tipo           |           Formato           |
| --------------- | -------------------------------------------------------------------------------------------- | :------: | :-------: | :---------------------: | :-------------------------: |
| id              | Código de indentificación asignado por Trawlingweb a cada publicación rastreada.             |    No    |    No     |         Cadena          |                             |
| title           | Título de la publicación.                                                                    |    Si    |    No     |         Cadena          |                             |
| text            | Cuerpo de texto de la publicación.                                                           |    Si    |    No     |         Cadena          |                             |
| published       | Fecha de publicación.                                                                        |    Si    |    Si     |          Fecha          |        ISO 8601-UTC         |
| crawled         | Fecha de captura. La zona horaria es GMT +1                                                  |    Si    |    Si     |         Entero          | UNIX Timestamp milisegundos |
| url             | Dirección web de la publicación                                                              |    No    |    No     |         Cadena          |                             |
| author          | Autor de la publicación                                                                      |    Si    |    No     |         Cadena          |                             |
| language        | Idioma de la publicación                                                                     |    Si    |    No     |         Cadena          |          ISO 639-1          |
| domain          | Dominio web donde se ha encontrado la publicación.                                           |    Si    |    No     |         Cadena          |                             |
| site            | Sitio web donde se ha encontrado la publicación.                                             |    Si    |    No     |         Cadena          |                             |
| site_type       | Tipo de sitio web segun el tipo de contenidos publicados (news, blogs, discusions y general) |    Si    |    No     |         Cadena          |                             |
| site_language   | Idioma del sitio web.                                                                        |    Si    |    No     |         Cadena          |          ISO 639-1          |
| site_country    | País del sitio web.                                                                          |    Si    |    No     |         Cadena          |         ISO 3166-2          |
| site_region     | Región del sitio web                                                                         |    Si    |    No     |         Cadena          |        ISO 3166-2:ES        |
| site_section    | Sección del sitio web donde se ha encontrado la publicación.                                 |    No    |    No     |         Cadena          |                             |
| section         | Sección en la que se ha encontrado la publicación                                            |    No    |    No     |         Cadena          |                             |
| value           | Valor económico estimado                                                                     |    No    |    No     | Número en coma flotante |                             |
| rank            | Ranking del dominio                                                                          |    No    |    No     |         Entero          |                             |
| unique_visitors | Número de visitantes únicos estimados                                                        |    No    |    No     |         Entero          |                             |

## Datos de petición

| Datos        | Descripción                                                             |  Tipo  |
| :----------- | :---------------------------------------------------------------------- | :----: |
| requestLeft  | Total de consultas pendientes de la subscripción                        | Entero |
| totalResults | Total de resultados encontrados por la consulta                         | Entero |
| restResults  | Total de resultados encontrados pendientes de entrega                   | Entero |
| next         | URL para continuar con la paginación y así obtener todos los resultados | Cadena |

## Ejemplo de respuesta en formato json:

```
"json"
"response" : {
    "data" : [{
        "id" : "...",
        "title" : "...",
        "text" : "...",
        "published" : "...",
        "crawled" : "...",
        "url" : "...",
        "author" : "...",
        "language" : "...",
        "domain" : "...",
        "site" : "...",
        "site_type" : "...",
        "site_language" : "...",
        "site_country" : "...",
        "site_region" : "...",
        "site_section" : "...",
        "section" : "...",
        "value" : "...",
        "rank" : "...",
        "unique_visitors" : "..."
    }],
    "requestLeft" : "...",
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

### A continuación se muestra un ejemplo de salida de una llamada a la API. Esta salida incluye información sobre los resultados restantes, el número total de resultados y la URL para obtener los siguientes resultados.

```
requestLeft	9999999
totalResults	295404987
restResults	295404887
next	"http://api.trawlingweb.com/?token=0000000000000000000000000000&q=casa&ts=1517443760316&tsi=1524818189854"

```


# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)