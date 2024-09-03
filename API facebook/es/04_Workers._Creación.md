# API Facebook - Método POST /create

Permite crear nuevos Workers con sus palabras.

# ¿Qué es un Worker?

Un Worker en TrawlingWeb es una entidad configurada por el usuario para realizar búsquedas específicas en redes sociales utilizando Palabras Clave. Estas Palabras Clave son términos de búsqueda configurados dentro del Worker y se basan en los créditos contratados (1 crédito = 1 Palabra Clave).

## Creación y Configuración de Workers

El usuario puede crear y definir los términos de búsqueda para cada Worker directamente en el dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) o utilizando el método proporcionado por la API. Una vez creado un Worker, este comienza su despliegue para iniciar su labor de configuración, que puede tardar hasta una hora.

## Funcionalidad de los Workers

* **Palabras clave**: Los Workers funcionan como una lista de palabras clave. Usan las Palabras Clave configuradas para realizar búsquedas en redes sociales.
* **Proceso de búsqueda**: Los Workers entregan las palabras clave a las arañas de TrawlingWeb para que ejecuten sus búsquedas en la red social.
* **Proceso de entrega**: Cada vez que el cliente llama al Worker, este utiliza la lista de palabras clave para lanzar la búsqueda contra la base de datos de resultados obtenidos por TrawlingWeb y recuperar solo aquellos resultados que tienen relación con la lista de palabras clave.

Implementar y gestionar Workers de manera eficiente permite a los usuarios maximizar la relevancia y precisión de los datos capturados, adaptándose a las necesidades específicas de sus análisis y monitoreo en redes sociales.


# Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://facebook.trawlingweb.com/create/?token={APIKEY}
```

## Parámetros PATH:

| Elemento  | Descripción                                 |
| :-------- | :------------------------------------------ |
| protocolo | Puede ser tanto **http** como **https**     |
| dominio   | Dirección de la API Facebook.trawlingweb.com |
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

Una vez lanzada una petición al API de Facebook éste devolverá una respuesta estructurada de la siguiente forma:

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

```
json
"response" : {
    "error" : "..."
}
```
# Mejores búsquedas con la sintaxy de Facebook

Facebook utiliza su propia sintaxis avanzada para ejecutar búsquedas específicas y detalladas dentro de su plataforma. Esta sintaxis permite filtrar resultados por palabras clave, hashtags, menciones, ubicaciones y fechas, entre otros parámetros. Además, al definir palabras clave para un Worker, es posible utilizar esta misma sintaxis para lanzar consultas precisas contra el buscador de Facebook. Esto maximiza la eficiencia y relevancia de los datos capturados por cada Worker, facilitando una monitorización y análisis más efectivos de las conversaciones en Facebook.

Aquí tienes un listado de los elementos que puedes combinar con tus palabras clave al crearlas dentro de un worker:

| Tipo              | Descripción                                                                          | Ejemplo                   |
| ----------------- | :----------------------------------------------------------------------------------- | :------------------------ |
| Hashtag           | Términos referenciados con la almohadilla #                                          | #pepsi                     |
| Arroba            | Usuarios referenciados con la arroba @                                               | @cocacola                     |
| Cadena simple     | Palabra con términos alfanuméricos sin caracteres especiales                         | Studio54                  |
| Cadena complejas  | Palabras con términos alfanuméricos sin caracteres especiales separadas por espacios | Cocoa Cola 2019          |
| Búsqueda exacta   | Palabras o frases específicas entre comillas                                         | "cocacola con hielo"      |
| Búsqueda con OR   | Palabras múltiples separadas por Espacio (__) para ampliar resultados                          | Cocacola (__) Pepsi   |
| Hashtag específico| Búsqueda de hashtags específicos                                                     | #openai                    |


## Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)


