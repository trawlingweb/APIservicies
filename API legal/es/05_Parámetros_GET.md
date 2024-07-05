# API Legal - Parámetros GET

## Método de consulta

Veamos la estructura de la consulta de ejemplo:

```
https://law.trawlingweb.com/?token={APIKEY}&q="ley"%20AND%20"economía"&ts=1518472804000
```

## Aquí podemos identificar:

| Elemento   | Descripción                              |
| :--------- | :--------------------------------------- |
| protocolo  | Puede ser tanto **http** como **https**  |
| dominio    | Dirección de la API boes.trawlingweb.com |
| parámetros | Parámetros de la consulta                |

## Elementos que especifican la información que se desea y la forma en que se quiere recibir:

| Parámetro | Descripción                                                                                                                                                                                                                | Default                                                 | Ejemplo                      |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------ | :--------------------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb.                                                                                                                                                                    | Valor obligatorio                                       | ?token={APIKEY}              |
| q         | Expresión construida con palabras o expresiones clave que configura los filtros de búsqueda. Permite hacer combinaciones con los distintos tipos de filtros disponibles mediante los operadores booleanos _y_, _o_ y _no_. | Por defecto devuelve todas las publicaciones            | &q="domain=lavanguardia.com" |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos                                                                                                                                               | Delimita a 1 meses en el pasado a partir de la petición | &ts=1518472804000            |
