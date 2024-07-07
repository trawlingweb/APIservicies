# API Twitter - Método POST /create

Permite crear nuevos Workers con sus palabras.

# Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://twitter.trawlingweb.com/create/?token={APIKEY}
```

## Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API twitter.trawlingweb.com |
| metodo    | create                                      |

## Parámetros QUERY:

| Parámetro | Descripción                                              | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

## Parámetros BODY:

| Parámetro   | Descripción                            | Default           | Límites                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Descripción que ha de tener el Worker. | Valor obligatorio | Cadena no superior a 200 carácteres                       |
| words       | Palabras de búsqueda.                  | Valor obligatorio | El número de parablas no ha de superar el límite acordado |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Twitter éste devolverá una respuesta estructurada de la siguiente forma:

## Status 200 - Datos de la retorno

| Campo  | Descripción                          |  Tipo  |
| ------ | ------------------------------------ | :----: |
| worker | Identificador del Worker creado.     | Cadena |
| msg    | Descripción indicando acción exitosa | Cadena |

## Ejemplo de respuesta en formato json:

```json
"response" : {
    "worker" : "...",
    "msg" : "..."
}
```

## Status 400 - Datos de la retorno

| Campo | Descripción           |  Tipo  |
| ----- | --------------------- | :----: |
| error | Descripción del error | Cadena |

## Ejemplo de respuesta en formato json:

```json
"response" : {
    "error" : "..."
}
```

# Características de los Workers

Podemos definir un Worker como una unidad de captura independiente.

El usuario crea y define que términos de búsqueda tiene cada Worker y lo puede hacer directamente en el dashboard ( https://dashboard.trawlingweb.com/workers) o usando este método.

Al crearse un Worker empieza su despliegue para iniciar su labor de captura, estructuración y almacenaje. Este despliegue puede tarda hasta una hora.


## Mejores búsquedas con la sintaxy de Twitter

Twitter utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de Twitter. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en Twitter.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo              | Descripción                                                                          | Ejemplo                   |
| ----------------- | :----------------------------------------------------------------------------------- | :------------------------ |
| Hashtag           | Términos referenciados con la almohadilla #                                          | #pepsi                     |
| Arroba            | Usuarios referenciados con la arroba @                                               | @cocacola                     |
| Cadena simple     | Palabra con términos alfanuméricos sin caracteres especiales                         | Studio54                  |
| Cadena complejas  | Palabras con términos alfanuméricos sin caracteres especiales separadas por espacios | Cocoa Cola 2019          |
| Búsqueda exacta   | Palabras o frases específicas entre comillas                                         | "cocacola con hielo"      |
| Búsqueda con OR   | Palabras múltiples separadas por OR para ampliar resultados                          | Cocacola OR Pepsi   |
| Sin palabras (NOT)      | Excluye palabras específicas de la búsqueda                                          | Cocacola -pepsi               |
| Hashtag específico| Búsqueda de hashtags específicos                                                     | #openai                    |
| Desde una cuenta  | Búsqueda de tweets enviados por una cuenta específica                                | from:cocacola         |
| A una cuenta      | Búsqueda de tweets enviados a una cuenta específica                                  | to:pepsi           |
| Mención de cuenta | Búsqueda de tweets que mencionan una cuenta específica                               | @cocacola             |
| Near ubicación    | Búsqueda de tweets enviados cerca de una ubicación específica                        | "comprar cocacola" near:"Argentina" |
| Dentro de radio   | Búsqueda de tweets enviados dentro de un radio específico                            | cocacola near:lima within:15km |
| Desde fecha       | Búsqueda de tweets enviados desde una fecha específica                               | cocacola since:2022-02-17  |
| Hasta fecha       | Búsqueda de tweets enviados hasta una fecha específica                               | pepsi until:2022-02-17 |
| Pregunta          | Búsqueda de tweets que contienen preguntas                                           | pepsi ?                |
| Con enlaces       | Búsqueda de tweets que contienen enlaces                                             | cocacola filter:links    |
| Fuente específica | Búsqueda de tweets publicados desde una fuente específica                            | pepsi source:twitterfeed |


## Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

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

