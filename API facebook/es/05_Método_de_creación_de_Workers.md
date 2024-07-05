# API Facebook - Método POST /create

Permite crear nuevos Workers con sus palabras.

# Parámetros POST

Veamos la estructura de la consulta de ejemplo:

```
https://facebook.trawlingweb.com/create/?token={APIKEY}
```

## Parámetros PATH:

| Elemento  | Descripción                                  |
| :-------- | :------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**      |
| dominio   | Dirección de la API facebook.trawlingweb.com |
| metodo    | create                                       |

## Parámetros QUERY:

| Parámetro | Descripción                                              | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb . | Valor obligatorio | ?token={APIKEY} |

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

```json
"response" : {
    "error" : "..."
}
```

# Características de los Workers

Podemos definir un Worker como una unidad de captura y almacenaje independiente.

El usuario crea y define que términos de búsqueda tiene cada Worker y lo puede hacer directamente en el dashboard ( https://dashboard.trawlingweb.com/workers) o usando este método.

Al crearse un Worker empieza su despliegue para iniciar su labor de captura, estructuración y almacenaje. Este despliegue puede tarda hasta una hora.

Cada Worker dispone de una base de datos independiente y un control de resultados duplicados específico.

## Características de las palabras definidas por el usuario

| Tipo             | Descripción                                                                          | Ejemplo          |
| ---------------- | :----------------------------------------------------------------------------------- | :--------------- |
| hastag           | Términos referenciados con la almohadilla #                                          | #casa            |
| Arroba           | Usuarios referenciados con la arroba @                                               | @pepe            |
| Cadena simple    | Palabra con términos alfanuméricos sin carácteres especiales                         | Studio54         |
| Cadena complejas | Palabras con términos alfanuméricos sin carácteres especiales separadas por espacios | Casa Blanca 2019 |

## Caracteres reservados en palabras de búsqueda

> Los caracteres reservados son: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -
