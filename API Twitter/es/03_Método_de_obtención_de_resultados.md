# API Twitter - Método GET /posts

Permite obtener resultado capturados de cada Worker configurado de Twitter.
Se pueden usar delimitadores temporales para acotar el contenido devuelto.

# Parámetros GET

La llamada a la API se construye a partir de la estructura básica:

```
https://twitter.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## Parámetros PATH

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API twitter.trawlingweb.com   |
| método    | posts                                         |
| workerid  | Identificador que permite acceder a un worker específico y recuperar los resultados generados por las palabras clave configuradas en él. Funciona como una biblioteca o lista de palabras clave, permitiendo obtener resultados relevantes basados en dichas palabras clave. |


## Parámetros QUERY

| Parámetro | Descripción                                                                  | Default                                                 | Ejemplo            |
| :-------- | :--------------------------------------------------------------------------- | :------------------------------------------------------ | :----------------- |
| token     | APIKEY para validar y acceder al sistema de TrawlingWeb. Cada usuario tiene su propia APIKEY individual e intransferible, vinculada a sus servicios y características.           | Valor obligatorio                                       | ?token={APIKEY}    |
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

# Uso de Consultas Booleanas Básicas en el API de Twitter de TrawlingWeb

Las APIs de TrawlingWeb aceptan consultas booleanas combinadas con expresiones de la sintaxis de Lucene. A continuación, mostramos algunos ejemplos prácticos que te ayudarán a tener una mejor experiencia y optimizar tus búsquedas y resultados al utilizar la API de Twitter.

Recuerda que estas expresiones booleanas solo pueden utilizarse dentro del parámetro q= en la llamada a la API y deben combinarse con los filtros y parámetros PATH necesarios.

## Operadores Booleanos esenciales AND, OR y NOT

Las consultas booleanas permiten combinar palabras clave o frases mediante operadores específicos. A continuación, te presentamos los operadores disponibles y algunos ejemplos útiles:

|  Operador   | Uso                                                                                                    |       Ejemplo        |
| :---------: | :----------------------------------------------------------------------------------------------------- | :------------------: |
| x **AND** y | "**x**" e "**y**" aparecerán en los documentos recuperados.                                            | "Mesi" AND "Girona"  |
| x **OR** y  | En los documentos recuperados, aparecerá "**x**", "**y**" o ambos. Se recomienda el uso de paréntesis. | ("Mesi" OR "Girona") |
|  **NOT** x  | No se recuperarán los documentos que incluyan "**x**".                                                 |      NOT "Mesi"      |

### Paréntesis

Utiliza paréntesis para encapsular declaraciones OR y asegurar que los motores de búsqueda ejecuten la consulta correctamente. El operador OR se interpreta como "Me gustaría al menos uno de estos términos."

Por ejemplo: _(Barcelona OR Madrid OR París)_

### Comillas

Las comillas deben utilizarse para buscar frases exactas de más de una palabra. Sin comillas, podrías obtener documentos con las palabras divididas en componentes individuales.

Por ejemplo: _Casa Blanca_

Sin comillas, los resultados podrían incluir páginas que contengan _Casa_ y _Blanca_, pero no necesariamente juntas. Usando comillas, indicas al sistema que solo debe devolver páginas que incluyan la frase exacta en ese orden.

Por ejemplo: _"Casa Blanca"_

### Wildcards

Puedes utilizar un asterisco (\*) para reemplazar algunos caracteres en la construcción de una consulta.

Por ejemplo:

- lavang\* (devolverá lavanguardia)
- \*pais (devolverá elpais)

El asterisco ayuda a crear sentencias largas o a buscar expresiones aunque se desconozca su forma completa.

### Más Información

Para más detalles, consulta el manual completo de sintaxis de Lucene ([aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)), que es la base de nuestro motor de búsqueda.

---

## Sintaxis de Consultas de Lucene

Las APIs de TrawlingWeb permiten realizar consultas que pueden contener operadores booleanos basados en la sintaxis de Lucene, ofreciendo una poderosa herramienta para realizar búsquedas complejas y precisas. La sintaxis de consultas de Lucene está diseñada para ser intuitiva y expresiva. A continuación, te presentamos algunas características clave y ejemplos útiles para optimizar tu experiencia de usuario:

### Otras sintaxis útiles

1.  **Consulta de Término**: Busca un término específico.

    ```
    cocacola
    ```

2.  **Consulta de Frase**: Busca una frase exacta encerrándola entre comillas dobles.

    ```
    "coca cola con gusto a cereza"
    ```

3.  **Consulta con Comodines**: Usa `?` para reemplazar un solo carácter o `*` para reemplazar cero o más caracteres.

    ```
    - ambigu? : (devolveria ambiguO o ambiguA)
    - ejem* : (devolveria entre otros, ejemPLO, ejemPLOS, ejemPLAR, ejemPLIZANTE..etc)
    ```

4.  **Operadores Booleanos**
    Usa `AND`, `OR` y `NOT` para combinar múltiples términos o frases.

        Ejemplos

        AND: Este operador se usa para buscar registros que contengan ambos términos o frases.

        Mcdonalds AND "Burger King"
        
        OR: Este operador se usa para buscar registros que contengan al menos uno de los términos o frases.

        Mcdonalds OR "Burger King"
        
        NOT: Este operador se usa para excluir registros que contengan el término o frase siguiente.

        Mcdonalds AND NOT "Burger King"

        

5. **Consultas Específicas de atributo**: Especifica atributo para buscar en partes particulares del documento.
   ```
   title:ejemplo
   text:"frase exacta"
   ```

### Ejemplso útiles de agrupación de elementos de búsqueda

(...) Usa paréntesis para agrupar cláusulas y formar subconsultas.

```
(coacola OR pepsi) AND (finanzas NOT delito)
```

### Ejemplos de consultas Lucene más utilizadas por nuestros clientes

Aquí tienes algunos ejemplos de consultas para ilustrar el uso de la sintaxis de Lucene en nuestra API de Noticias:

- Búsquedas de Proximidad (o near): Encuentra palabras que estén a cierta distancia entre sí.

   ```
   "delito financiero"~5
   ```
   el match será si se encuentran las dos palabras y estas se encuentra ubicadas a una distancia máxima de 5 caractéres entre estas

- Buscar artículos que contengan la palabra "tecnología":

  ```
  tecnología
  ```

- Buscar artículos con la frase exacta "inteligencia artificial":

  ```
  "inteligencia artificial"
  ```

- Buscar artículos con "clima" en el título y "cambio" en el contenido:

  ```
  title:clima AND contenido:cambio
  ```

- Buscar artículos que mencionen "economía" pero no "recesión":
  ```
  economía NOT recesión
  ```

## Conclusión

Usar la sintaxis de consultas de Lucene con la API de Noticias de TrawlingWeb te permite crear búsquedas precisas y complejas, asegurando que recuperes los datos más relevantes. Para una comprensión más completa de la sintaxis de consultas de Lucene, consulta la [documentación oficial de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

Si tienes alguna pregunta o necesitas más asistencia, por favor contacta a nuestro equipo de soporte.

---

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
- [Correo SAT](mailto:support@trawlingweb.com)
- [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
- [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
- [Correo Ventas](mailto:sales@trawlingweb.com)


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
