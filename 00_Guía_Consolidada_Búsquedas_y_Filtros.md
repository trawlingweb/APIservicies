# Guía Consolidada - Búsquedas y Filtros de todas las APIs

Este documento consolida la información sobre creación de Workers y parámetros de búsqueda/filtrado de todas las APIs de TrawlingWeb.

---

# API Twitter - Método POST /create

Permite crear nuevos Workers con sus palabras.

## ¿Qué es un Worker?

Un Worker en TrawlingWeb es una entidad configurada por el usuario para realizar búsquedas específicas en redes sociales utilizando Palabras Clave. Estas Palabras Clave son términos de búsqueda configurados dentro del Worker y se basan en los créditos contratados (1 crédito = 1 Palabra Clave).

### Creación y Configuración de Workers

El usuario puede crear y definir los términos de búsqueda para cada Worker directamente en el dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) o utilizando el método proporcionado por la API. Una vez creado un Worker, este comienza su despliegue para iniciar su labor de configuración, que puede tardar hasta una hora.

### Funcionalidad de los Workers

- **Palabras clave**: Los Workers funcionan como una lista de palabras clave. Usan las Palabras Clave configuradas para realizar búsquedas en redes sociales.
- **Proceso de búsqueda**: Los Workers entregan las palabras clave a las arañas de TrawlingWeb para que ejecuten sus búsquedas en la red social.
- **Proceso de entrega**: Cada vez que el cliente llama al Worker, este utiliza la lista de palabras clave para lanzar la búsqueda contra la base de datos de resultados obtenidos por TrawlingWeb y recuperar solo aquellos resultados que tienen relación con la lista de palabras clave.

Implementar y gestionar Workers de manera eficiente permite a los usuarios maximizar la relevancia y precisión de los datos capturados, adaptándose a las necesidades específicas de sus análisis y monitoreo en redes sociales.

## Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://twitter.trawlingweb.com/create/?token={APIKEY}
```

### Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API twitter.trawlingweb.com |
| metodo    | create                                      |

### Parámetros QUERY:

| Parámetro | Descripción                                             | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------ | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

### Parámetros BODY:

| Parámetro   | Descripción                            | Default           | Límites                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Descripción que ha de tener el Worker. | Valor obligatorio | Cadena no superior a 200 carácteres                       |
| words       | Palabras de búsqueda.                  | Valor obligatorio | El número de parablas no ha de superar el límite acordado |

### Estructura del parámetro words

El parámetro `words` debe enviarse como un **array JSON** de cadenas de texto, donde cada elemento del array representa una Palabra Clave. Cada Palabra Clave puede contener sintaxis avanzada de Twitter (hashtags, menciones, operadores booleanos, filtros, etc.).

**Recomendación importante para búsquedas con `from:`**: Cuando necesites buscar tweets de múltiples cuentas, puedes encadenar hasta un máximo de 10 cuentas usando el operador OR dentro de una misma expresión. Esto permite optimizar el uso de créditos al agrupar múltiples cuentas en una sola Palabra Clave.

### Ejemplo de body en formato JSON:

```json
{
    "description": "Worker de ejemplo para monitoreo de marcas",
    "words": [
        "from:cocacola OR from:pepsi OR from:trawlingweb",
        "cocacola",
        "#pepsi",
        "cocacola lang:fr"
    ]
}
```

En este ejemplo, el Worker se crea con 4 Palabras Clave:
1. Una búsqueda compleja con múltiples cuentas usando el operador OR (máximo 10 cuentas por expresión)
2. Una palabra simple: "cocacola"
3. Un hashtag: "#pepsi"
4. Una palabra con filtro de idioma: "cocacola lang:fr"

Cada elemento del array `words` consume 1 crédito (1 crédito = 1 Palabra Clave).

## Mejores búsquedas con la sintaxis de Twitter

Twitter utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de Twitter. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en Twitter.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo                          | Descripción                                                                          | Ejemplo keyword                | Resultado                                                                           |
| ----------------------------- | :----------------------------------------------------------------------------------- | :----------------------------- | ----------------------------------------------------------------------------------- |
| Hashtag                       | Términos referenciados con la almohadilla #                                          | #pepsi                         | devolvera posts que contienen hashtag (#) pepsi                                     |
| Arroba                        | Usuarios referenciados con la arroba @                                               | @cocacola                      | devolevra postsen los qeu se haetiquetado/mencionado (@) cocacola                   |
| Cadena simple                 | Palabra con términos alfanuméricos sin caracteres especiales                         | Studio54                       | devolverá post qeu contienen la palabra "Studio54"                                  |
| Cadena complejas              | Palabras con términos alfanuméricos sin caracteres especiales separadas por espacios | Cocoa Cola 2019                | devolverá cualquier post que contenga alguna o todas estas las palabras del ejemplo |
| Búsqueda exacta               | Palabras o frases específicas entre comillas                                         | "cocacola con hielo"           | devolverá posts que contienen exactamente la frase "cocacola con hielo"             |
| Búsqueda con OR               | Palabras múltiples separadas por OR para ampliar resultados                          | Cocacola OR Pepsi              | devolverá posts que contienen "Cocacola" o "Pepsi" (o ambos)                       |
| Sin palabras (NOT)            | Excluye palabras específicas de la búsqueda                                          | Cocacola -pepsi                | devolverá posts que contienen "Cocacola" pero excluye aquellos que contienen "pepsi" |
| Hashtag específico            | Búsqueda de hashtags específicos                                                     | #openai                        | devolverá posts que contienen el hashtag (#) openai                                 |
| Desde una cuenta              | Búsqueda de tweets enviados por una cuenta específica. Se pueden encadenar hasta 10 cuentas con OR dentro de una misma expresión | from:cocacola                  | devolverá posts publicados por la cuenta @cocacola. Ejemplo con múltiples: `from:cuenta1 OR from:cuenta2 OR ... OR from:cuenta10` |
| A una cuenta                  | Búsqueda de tweets enviados a una cuenta específica                                  | to:pepsi                       | devolverá posts dirigidos a la cuenta @pepsi                                        |
| Mención de cuenta             | Búsqueda de tweets que mencionan una cuenta específica                               | @cocacola                      | devolverá posts en los que se ha etiquetado/mencionado (@) cocacola                |
| Near ubicación                | Búsqueda de tweets enviados cerca de una ubicación específica                        | "comprar cocacola" near:Quito  | devolverá posts que contienen "comprar cocacola" enviados cerca de Quito            |
| Dentro de radio               | Búsqueda de tweets enviados dentro de un radio específico                            | cocacola near:lima within:15km | devolverá posts que contienen "cocacola" enviados dentro de 15km de Lima           |
| Desde fecha                   | Búsqueda de tweets enviados desde una fecha específica                               | cocacola since:2022-02-17      | devolverá posts que contienen "cocacola" publicados desde el 17 de febrero de 2022  |
| Hasta fecha                   | Búsqueda de tweets enviados hasta una fecha específica                               | pepsi until:2022-02-17         | devolverá posts que contienen "pepsi" publicados hasta el 17 de febrero de 2022    |
| Pregunta                      | Búsqueda de tweets que contienen preguntas                                           | pepsi ?                        | devolverá posts que contienen "pepsi" y que son preguntas                          |
| Con enlaces                   | Búsqueda de tweets que contienen enlaces                                             | cocacola filter:links          | devolverá posts que contienen "cocacola" y que incluyen enlaces                    |
| Fuente específica             | Búsqueda de tweets publicados desde una fuente específica                            | pepsi source:twitterfeed       | devolverá posts que contienen "pepsi" publicados desde la fuente twitterfeed        |
| palabra con idioma específico | Búsqueda de tweets publicados en un idioma específico. Ha de ser en ISO Alpha II     | pepsi lang:fr                  | devolverá posts que contienen "pepsi" publicados en francés (ISO Alpha II: fr)      |

### Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

---

# API Facebook - Método POST /create

Permite crear nuevos Workers con sus palabras.

## ¿Qué es un Worker?

Un Worker en TrawlingWeb es una entidad configurada por el usuario para realizar búsquedas específicas en redes sociales utilizando Palabras Clave. Estas Palabras Clave son términos de búsqueda configurados dentro del Worker y se basan en los créditos contratados (1 crédito = 1 Palabra Clave).

### Creación y Configuración de Workers

El usuario puede crear y definir los términos de búsqueda para cada Worker directamente en el dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) o utilizando el método proporcionado por la API. Una vez creado un Worker, este comienza su despliegue para iniciar su labor de configuración, que puede tardar hasta una hora.

### Funcionalidad de los Workers

* **Palabras clave**: Los Workers funcionan como una lista de palabras clave. Usan las Palabras Clave configuradas para realizar búsquedas en redes sociales.
* **Proceso de búsqueda**: Los Workers entregan las palabras clave a las arañas de TrawlingWeb para que ejecuten sus búsquedas en la red social.
* **Proceso de entrega**: Cada vez que el cliente llama al Worker, este utiliza la lista de palabras clave para lanzar la búsqueda contra la base de datos de resultados obtenidos por TrawlingWeb y recuperar solo aquellos resultados que tienen relación con la lista de palabras clave.

Implementar y gestionar Workers de manera eficiente permite a los usuarios maximizar la relevancia y precisión de los datos capturados, adaptándose a las necesidades específicas de sus análisis y monitoreo en redes sociales.

## Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://facebook.trawlingweb.com/create/?token={APIKEY}
```

### Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API Facebook.trawlingweb.com |
| metodo    | create                                      |

### Parámetros QUERY:

| Parámetro | Descripción                                              | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

### Parámetros BODY:

| Parámetro   | Descripción                            | Default           | Límites                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Descripción que ha de tener el Worker. | Valor obligatorio | Cadena no superior a 200 carácteres                       |
| words       | Palabras de búsqueda.                  | Valor obligatorio | El número de parablas no ha de superar el límite acordado |

### Estructura del parámetro words

El parámetro `words` debe enviarse como un **array JSON** de cadenas de texto, donde cada elemento del array representa una Palabra Clave. Cada Palabra Clave puede contener sintaxis avanzada de Facebook (hashtags, menciones, operadores booleanos, etc.).

### Ejemplo de body en formato JSON:

```json
{
    "description": "Worker de ejemplo para monitoreo de marcas",
    "words": [
        "cocacola",
        "#pepsi",
        "@cocacola",
        "Cocacola (__) Pepsi",
        "\"cocacola con hielo\""
    ]
}
```

En este ejemplo, el Worker se crea con 5 Palabras Clave:
1. Una palabra simple: "cocacola"
2. Un hashtag: "#pepsi"
3. Una mención: "@cocacola"
4. Una búsqueda con OR usando (__): "Cocacola (__) Pepsi"
5. Una búsqueda exacta entre comillas: "cocacola con hielo"

Cada elemento del array `words` consume 1 crédito (1 crédito = 1 Palabra Clave).

## Mejores búsquedas con la sintaxis de Facebook

Facebook utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de Facebook. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en Facebook.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo              | Descripción                                                                          | Ejemplo keyword                | Resultado                                                                           |
| ----------------- | :----------------------------------------------------------------------------------- | :----------------------------- | ----------------------------------------------------------------------------------- |
| Hashtag           | Términos referenciados con la almohadilla #                                          | #pepsi                         | devolverá posts que contienen el hashtag (#) pepsi                                     |
| Arroba            | Usuarios referenciados con la arroba @                                               | @cocacola                      | devolverá posts en los que se ha etiquetado/mencionado (@) cocacola                   |
| Cadena simple     | Palabra con términos alfanuméricos sin caracteres especiales                         | Studio54                       | devolverá posts que contienen la palabra "Studio54"                                  |
| Cadena complejas  | Palabras con términos alfanuméricos sin caracteres especiales separadas por espacios | Cocoa Cola 2019                | devolverá cualquier post que contenga alguna o todas estas palabras del ejemplo |
| Búsqueda exacta   | Palabras o frases específicas entre comillas                                         | "cocacola con hielo"           | devolverá posts que contienen exactamente la frase "cocacola con hielo"             |
| Búsqueda con OR   | Palabras múltiples separadas por (__) para ampliar resultados                          | Cocacola (__) Pepsi            | devolverá posts que contienen "Cocacola" o "Pepsi" (o ambos)                       |
| Hashtag específico| Búsqueda de hashtags específicos                                                     | #openai                        | devolverá posts que contienen el hashtag (#) openai                                 |

### Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

---

# API Instagram - Método POST /create

Permite crear nuevos Workers con sus palabras.

## ¿Qué es un Worker?

Un Worker en TrawlingWeb es una entidad configurada por el usuario para realizar búsquedas específicas en redes sociales utilizando Palabras Clave. Estas Palabras Clave son términos de búsqueda configurados dentro del Worker y se basan en los créditos contratados (1 crédito = 1 Palabra Clave).

### Creación y Configuración de Workers

El usuario puede crear y definir los términos de búsqueda para cada Worker directamente en el dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) o utilizando el método proporcionado por la API. Una vez creado un Worker, este comienza su despliegue para iniciar su labor de configuración, que puede tardar hasta una hora.

### Funcionalidad de los Workers

* **Palabras clave**: Los Workers funcionan como una lista de palabras clave. Usan las Palabras Clave configuradas para realizar búsquedas en redes sociales.
* **Proceso de búsqueda**: Los Workers entregan las palabras clave a las arañas de TrawlingWeb para que ejecuten sus búsquedas en la red social.
* **Proceso de entrega**: Cada vez que el cliente llama al Worker, este utiliza la lista de palabras clave para lanzar la búsqueda contra la base de datos de resultados obtenidos por TrawlingWeb y recuperar solo aquellos resultados que tienen relación con la lista de palabras clave.

Implementar y gestionar Workers de manera eficiente permite a los usuarios maximizar la relevancia y precisión de los datos capturados, adaptándose a las necesidades específicas de sus análisis y monitoreo en redes sociales.

## Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://instagram.trawlingweb.com/create/?token={APIKEY}
```

### Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API Instagram.trawlingweb.com |
| metodo    | create                                      |

### Parámetros QUERY:

| Parámetro | Descripción                                              | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

### Parámetros BODY:

| Parámetro   | Descripción                            | Default           | Límites                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Descripción que ha de tener el Worker. | Valor obligatorio | Cadena no superior a 200 carácteres                       |
| words       | Palabras de búsqueda.                  | Valor obligatorio | El número de parablas no ha de superar el límite acordado |

### Estructura del parámetro words

El parámetro `words` debe enviarse como un **array JSON** de cadenas de texto, donde cada elemento del array representa una Palabra Clave. Cada Palabra Clave puede contener sintaxis avanzada de Instagram (hashtags, menciones, etc.).

### Ejemplo de body en formato JSON:

```json
{
    "description": "Worker de ejemplo para monitoreo de marcas",
    "words": [
        "#pepsi",
        "@cocacola",
        "#openai"
    ]
}
```

En este ejemplo, el Worker se crea con 3 Palabras Clave:
1. Un hashtag: "#pepsi"
2. Una mención: "@cocacola"
3. Un hashtag específico: "#openai"

Cada elemento del array `words` consume 1 crédito (1 crédito = 1 Palabra Clave).

## Mejores búsquedas con la sintaxis de Instagram

Instagram utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de Instagram. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en Instagram.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo              | Descripción                                                                          | Ejemplo keyword                | Resultado                                                                           |
| ----------------- | :----------------------------------------------------------------------------------- | :----------------------------- | ----------------------------------------------------------------------------------- |
| Hashtag           | Términos referenciados con la almohadilla #                                          | #pepsi                         | devolverá posts que contienen el hashtag (#) pepsi                                     |
| Arroba            | Usuarios referenciados con la arroba @                                               | @cocacola                      | devolverá posts en los que se ha etiquetado/mencionado (@) cocacola                   |
| Hashtag específico| Búsqueda de hashtags específicos                                                     | #openai                        | devolverá posts que contienen el hashtag (#) openai                                 |

### Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

---

# API TikTok - Método POST /create

Permite crear nuevos Workers con sus palabras.

## ¿Qué es un Worker?

Un Worker en TrawlingWeb es una entidad configurada por el usuario para realizar búsquedas específicas en redes sociales utilizando Palabras Clave. Estas Palabras Clave son términos de búsqueda configurados dentro del Worker y se basan en los créditos contratados (1 crédito = 1 Palabra Clave).

### Creación y Configuración de Workers

El usuario puede crear y definir los términos de búsqueda para cada Worker directamente en el dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) o utilizando el método proporcionado por la API. Una vez creado un Worker, este comienza su despliegue para iniciar su labor de configuración, que puede tardar hasta una hora.

### Funcionalidad de los Workers

* **Palabras clave**: Los Workers funcionan como una lista de palabras clave. Usan las Palabras Clave configuradas para realizar búsquedas en redes sociales.
* **Proceso de búsqueda**: Los Workers entregan las palabras clave a las arañas de TrawlingWeb para que ejecuten sus búsquedas en la red social.
* **Proceso de entrega**: Cada vez que el cliente llama al Worker, este utiliza la lista de palabras clave para lanzar la búsqueda contra la base de datos de resultados obtenidos por TrawlingWeb y recuperar solo aquellos resultados que tienen relación con la lista de palabras clave.

Implementar y gestionar Workers de manera eficiente permite a los usuarios maximizar la relevancia y precisión de los datos capturados, adaptándose a las necesidades específicas de sus análisis y monitoreo en redes sociales.

## Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://tiktok.trawlingweb.com/create/?token={APIKEY}
```

### Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API TikTok.trawlingweb.com |
| metodo    | create                                      |

### Parámetros QUERY:

| Parámetro | Descripción                                              | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

### Parámetros BODY:

| Parámetro   | Descripción                            | Default           | Límites                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Descripción que ha de tener el Worker. | Valor obligatorio | Cadena no superior a 200 carácteres                       |
| words       | Palabras de búsqueda.                  | Valor obligatorio | El número de parablas no ha de superar el límite acordado |

### Estructura del parámetro words

El parámetro `words` debe enviarse como un **array JSON** de cadenas de texto, donde cada elemento del array representa una Palabra Clave. Cada Palabra Clave puede contener sintaxis avanzada de TikTok (hashtags, menciones, etc.).

### Ejemplo de body en formato JSON:

```json
{
    "description": "Worker de ejemplo para monitoreo de marcas",
    "words": [
        "#pepsi",
        "@cocacola",
        "#openai"
    ]
}
```

En este ejemplo, el Worker se crea con 3 Palabras Clave:
1. Un hashtag: "#pepsi"
2. Una mención: "@cocacola"
3. Un hashtag específico: "#openai"

Cada elemento del array `words` consume 1 crédito (1 crédito = 1 Palabra Clave).

## Mejores búsquedas con la sintaxis de TikTok

TikTok utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de TikTok. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en TikTok.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo              | Descripción                                                                          | Ejemplo keyword                | Resultado                                                                           |
| ----------------- | :----------------------------------------------------------------------------------- | :----------------------------- | ----------------------------------------------------------------------------------- |
| Hashtag           | Términos referenciados con la almohadilla #                                          | #pepsi                         | devolverá posts que contienen el hashtag (#) pepsi                                     |
| Arroba            | Usuarios referenciados con la arroba @                                               | @cocacola                      | devolverá posts en los que se ha etiquetado/mencionado (@) cocacola                   |
| Hashtag específico| Búsqueda de hashtags específicos                                                     | #openai                        | devolverá posts que contienen el hashtag (#) openai                                 |

### Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

---

# API NEWS & BLOGS - Parámetro de filtrado

## API NEWS & BLOGS - Parámetros de Filtrado

Los filtros son atributos asignados por TrawlingWeb a cada elemento durante su proceso de auditoría de fuentes y resultados. Estos filtros permiten especificar criterios detallados para obtener únicamente los datos que necesitas. Al aplicar estos filtros en tus consultas, puedes afinar los resultados para que se ajusten mejor a tus requisitos específicos. A continuación, se describen los filtros disponibles:

| Filtro        | Descripción                                                                                                                                               |
| :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| site          | Sitio web del que queremos o no queremos obtener datos.                                                                                                   |
| domain        | Dominio del que queremos o no queremos recuperar datos.                                                                                                   |
| title         | Palabras o expresiones que deben o no deben aparecer en los títulos de las publicaciones deseadas.                                                        |
| text          | Palabras de deben aparecer o no deben aparecer en las publicaciones deseadas.                                                                             |
| language      | Idioma de las publicaciones que deseamos incluir o excluir en la recuperación. Ver códigos de idioma [ISO 639-1](https://es.wikipedia.org/wiki/ISO_639-1) |
| site_language | Idioma del sitio web: en (inglés), es (español), fr (francés), ...                                                                                        |
| site_country  | País del sitio web. Ver códigos de país según [ISO-3166-2](https://es.wikipedia.org/wiki/ISO_3166-2).                                                     |
| site_region   | Región del sitio web: [ISO-3166-2](https://es.wikipedia.org/wiki/ISO_3166-2).                                                                             |
| author        | Autor de la publicación: joanfuster, angelgabilondo, etc                                                                                                  |
| published     | Fecha de publicación (en milisegundos). [Conversor](http://www.onlineconversion.com/unix_time.htm)                                                        |
| crawled       | Fecha de restreo (en milisegundos). [Conversor](http://www.onlineconversion.com/unix_time.htm)                                                            |
| site_type     | Tipo del sitio web: general, news, blog o discussion.                                                                                                     |

## La forma de asignar una expresión de filtro

    q = "(_filtro1_: __valor1__) operador (_filtro2_ : valor2) operador ... (_filtroN_ : valorN)"

> En esta expresión se ha añadido espacios entre los términos con el fin de claridad pero hay que evitarlos durante la realización de consultas.

## Más información sobre las posibilidades de combinación y búsqueda

Para más información sobre operadores y sintaxis de Lucene, puede consultar la sección 07: Mejores Prácticas. También puede consultar el manual completo de sintaxis de Lucene [aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html), siendo esta nuestra base de motor de búsqueda.

## Escapar caracteres reservados

Si necesita utilizar cualquiera de los caracteres que funcionan como operadores de su propia consulta (y no como operadores), entonces usted debe escaparlos con una barra invertida inicial.
Por ejemplo, para buscar url:https://www.linkedin.com , lo que se necesita para escribir su consulta como url:https \:\ / \ / www.linkedin.com

> Los caracteres reservados son: + - = && || > <! () {} [] ^ "~ \*?: \ /

El no poder escapar de estos caracteres especiales correctamente podría dar lugar a un error de sintaxis que impide que la consulta se ejecute de forma correcta.

## Ejemplos de filtros y booleanas dentro de **q=**

Como hemos explicado en la sección 03 Consultas, las APIs de TrawlingWeb aceptan consultas booleanas combinadas con expresiones de la sintaxis de Lucene.

La `q=` permite el filtrado y optimización de la consulta para obtener los mejores resultados posibles. Dentro de `q=` puedes utilizar parámetros de filtrado (ver ), que son atributos asignados por TrawlingWeb a cada elemento, así como expresiones booleanas que son características de los contenidos capturados. 

Recuerda que en la sección 03 Consultas hay una lista más completa de expresiones booleanas que puedes combinar con los filtros dentro de `q=`. A continuación, algunos ejemplos de parámetros de filtrado.

| Ejemplo                                                               | Explicación                                                                                                                                                              |
| :-------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ```(site: elpais.com OR site: lavanguardia.com)```                         | Recuperar solo publicaciones de los sitios web elpais.com o lavanguardia.com o de los dos.                                                                               |
| ```NOT (site:yahoo.com AND site:google.com)```                              | Recuperar publicaciones de todos los sitios web excepto de los sitios yahoo.com y google.com.                                                                            |
| ```((title:rajoy AND (text:España OR text:Morales)) NOT title:españoles)``` | Recuperar solo publicaciones cuyo título incluya las palabras "rajoy" y (o "españa" o "morales") y excluya "españoles" .                                                 |
| ```(language:es OR language:cat)```                                         | Recuperar solo publicaciones cuyo idioma sea español o catalán.                                                                                                          |
| ```(site_language:es OR site_language:cat)```                               | Recuperar solo publicaciones de sitios web cuyo idioma sea español o catalán.                                                                                            |
| ```NOT (site_language:es OR site_language:cat)```                           | Recuperar todas la publicaciones excepto aquellas publicadas en sitios web cuyo idioma sea español o catalán.                                                            |
| ```author:Pedrolo```                                                        | Recuperar solo documentos cuyo autor incluya "Pedrolo".                                                                                                                  |
| ```(site_type:news OR site_type:blogs)```                                   | Recuperar solo publicaciones de sitios web de noticias o de blogs.                                                                                                       |
| ```NOT (site_type:general)```                                               | Recuperar publicaciones de sitios web todos de los tipos excepto de los que solo ofrecen información general, es decir, obtener datos solo de sitios web especializados. |

---

# API YOUTUBE - Consultas básicas

El API permite las mismas consultas que se realizan al actual buscador de la web de Youtube. Los criterios en que se aplican al filtrar los vídeos son establecidos por la propia Youtube.

## Booleanas

| Operador | Uso                                                                                                                                                                                       |       Ejemplo       |
| :------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----------------: |
| **AND**  | El operador **AND** es un operador implícito al incluir varios términos con espacio. aparecerán en los vídeos recuperados. También se puede usar el símbolo **+**                         |  "Messi" "Girona"   |
|  **OR**  | El operador **OR** se estable con **\|** . Los vídeos recuperados, o bien aparecerá "**x**", o bien aparecerà "**y**" o bien las dos. Se recomienda el uso de **()** para evitar errores. | ("Messi"\|"Girona") |
| **NOT**  | El operador **NOT** se establece con **-** . No se recuperan los documentos que incluyen "**x**"                                                                                          |       -Messi        |

## Los paréntesis

Utilice paréntesis para encapsular declaraciones OR para que los motores de búsqueda ejecuten la consulta de forma correcta.

Por ejemplo: _(Barcelona|Madrid|París)_

## Otros términos filtrables

### Búsqueda de vídeos con términos juntos

    Tortilla patata casera

### Búsqueda de vídeos con términos en el título

    allintitle:Walt Disney

### Búsqueda de vídeos que contienen combinaciones de palabras

    "U2 Melbourne 2006"

### Búsqueda de vídeos en canal

    Elvis Presley, channel

### Búsqueda de vídeos peliculas

    Charlie Chaplin, movie

### Búsqueda de vídeos en 4k

    Tokio, 4k

### Búsqueda de vídeos en HD

    Trailer de Star Trek, hd

### Búsqueda de vídeos en SD

    Moscú, sd

### Búsqueda de vídeos en ED

    Madagascar, 3d

### Búsqueda de vídeos por duración inferior a 2 minutos

    Simpsons, short

### Búsqueda de vídeos por duración mínima de 20 minutos

    Spiderman, long

### Búsqueda de vídeos en directo

    zoo, live

### Búsqueda de vídeos por tiempo

    noticias, today
    noticias, this week
    noticias, this month
    noticias, this year

### Búsqueda de vídeos en canales oficiales

    The show must go on, partner

### Búsqueda de vídeos en playlist

    Queen, playlist

### Búsqueda de vídeos usando el concepto booleano (NOT)

    android -china

### Búsqueda de vídeos usando el concepto booleano (AND)

    Barcelona AND Paris

### Búsqueda de vídeos usando el concepto booleano (OR)

    Barcelona OR Paris

### Búsqueda de vídeos combinando los anteriores

    (Barcelona AND Paris) -messi ,4k , long

---

# Contacto

Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)

