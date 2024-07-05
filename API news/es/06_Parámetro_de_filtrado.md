# API NEWS & BLOGS - Parámetro de filtrado

Los siguientes filtros le permitirán obtener únicamente los datos que necesita.

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

## La forma de assignar una expresion de filtro

    q = "(_filtro1_: __valor1__) operador (_filtro2_ : valor2) operador ... (_filtroN_ : valorN)"

> En esta expresión se ha añadido espacios entre los téminos con el fines de claridad pero hay que evitarlos durante la realización de cosultas.

## Más información sobre las posibilidades de convinación y búsqueda

Para más información puede consultar el manual completo de syntaxis de Lucene ( [aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html) ) siendo esta nuestra base de motor de búsqueda.

## Escapar caracteres reservados

Si necesita utilizar cualquiera de los caracteres que funcionan como operadores de su propia consulta (y no como operadores), entonces usted debe escaparlos con una barra invertida inicial.
Por ejemplo, para buscar url:https://www.linkedin.com , lo que se necesita para escribir su consulta como url:https \:\ / \ / www.linkedin.com

> Los caracteres reservados son: + - = && || > <! () {} [] ^ "~ \*?: \ /

El no poder escapar de estos caracteres especiales correctamente podría dar lugar a un error de sintaxis que impide que la consulta se ejecute de forma correcta.

## Ejemplos de filtros **q**

| Ejemplo                                                               | Explicación                                                                                                                                                              |
| :-------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| (site: elpais.com OR site: lavanguardia.com)                          | Recuperar solo publicaciones de los sitios web elpais.com o lavanguardia.com o de los dos.                                                                               |
| NOT (site:yahoo.com AND site:google.com)                              | Recuperar publicaciones de todos los sitios web excepto de los sitios yahoo.com y google.com.                                                                            |
| ((title:rajoy AND (text:España OR text:Morales)) NOT title:españoles) | Recuperar solo publicaciones cuyo título incluya las palabras "rajoy" y (o "españa" o "morales") y excluya "españoles" .                                                 |
| (language:es OR language:cat)                                         | Recuperar solo publicaciones cuyo idioma sea español o catalán.                                                                                                          |
| (site_language:es OR site_language:cat)                               | Recuperar solo publicaciones de sitios web cuyo idioma sea español o catalán.                                                                                            |
| NOT (site_language:es OR site_language:cat)                           | Recuperar todas la publicaciones excepto aquellas publicadas en sitios web cuyo idioma sea español o catalán.                                                            |
| author:Pedrolo                                                        | Recuperar solo documentos cuyo autor incluya "Pedrolo".                                                                                                                  |
| (site_type:news OR site_type:blogs)                                   | Recuperar solo publicaciones de sitios web de noticias o de blogs.                                                                                                       |
| NOT (site_type:general)                                               | Recuperar publicaciones de sitios web todos de los tipos excepto de los que solo ofrecen información general, es decir, obtener datos solo de sitios web especializados. |
