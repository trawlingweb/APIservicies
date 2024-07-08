# API Instagram - Método GET /workers

Permite obtener los Workers configurados por el usuario y los datos de los mismos

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

```
https://instagram.trawlingweb.com/workers/?token={APIKEY}
```

## Parámetros PATH:

| Elemento  | Descripción                                   |
| :-------- | :-------------------------------------------- |
| protocolo | Puede ser tanto **http** como **https**       |
| dominio   | Dirección de la API instagram.trawlingweb.com |
| metodo    | workers                                       |

## Parámetros QUERY:

| Parámetro | Descripción                                             | Default           | Ejemplo         |
| :-------- | :------------------------------------------------------ | :---------------- | :-------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb. | Valor obligatorio | ?token={APIKEY} |

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Instagram éste devolverá una respuesta estructurada de la siguiente forma:

## Datos de cada Worker

| Campo       | Descripción                                              | Buscable | Ordenable |  Tipo  |   Formato    |
| ----------- | -------------------------------------------------------- | :------: | :-------: | :----: | :----------: |
| id          | Código de indentificación del Worker                     |    No    |    No     | Cadena |              |
| type        | Tipo de Worker (facebook, instagram, twitter)            |    No    |    No     | Cadena |              |
| description | Descripción establedida por el usuario                   |    No    |    No     | Cadena |              |
| words       | Palabras de búsqueda                                     |    No    |    No     | Cadena |              |
| counter     | Número de publicaciones almacenadas                      |    No    |    No     | Entero |              |
| created_at  | Fecha de creación del Worker                             |    No    |    No     | Fecha  | ISO 8601-UTC |
| status      | Estatus de actividad del Worker ( 1 running , 0 stoped ) |    No    |    No     | Entero |              |

## Datos generales

| Campo       | Descripción                   | Buscable | Ordenable |  Tipo  | Formato |
| ----------- | ----------------------------- | :------: | :-------: | :----: | :-----: |
| workersLeft | Número de Workers disponibles |    No    |    No     | Entero |         |
| limit       | Número de Workers máximos     |    No    |    No     | Entero |         |

## Ejemplo de respuesta en formato json:

```json
"response" : {
    "workers" : [{
            "id" : "...",
            "type" : "...",
            "description" : "...",
            "words" : "...",
            "counter" : "...",
            "created_at" : "...",
            "status" : "..."
    }],
    "workersLeft" : "...",
    "limit" : "..."
}
```
