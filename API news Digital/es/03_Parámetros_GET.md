# API NEWS & BLOGS - Parámetros GET

### Introducción
En esta sección, se presenta una guía detallada sobre cómo construir y ejecutar consultas utilizando la API News & Blogs de TrawlingWeb. Esta API permite a los usuarios acceder a una amplia base de datos de contenidos capturados, filtrando y recuperando información específica mediante el uso de parámetros GET.

A continuación, se explican los métodos estándar para realizar consultas, desglosando cada componente de la URL de ejemplo. También se proporciona una tabla con una descripción exhaustiva de cada parámetro, su uso, valores predeterminados y ejemplos prácticos. Esta información es esencial para los desarrolladores y usuarios que buscan maximizar la eficiencia y precisión de sus consultas a la API.

## Métodos Standard
Veamos la estructura de la consulta de ejemplo:

```
https://api.trawlingweb.com/?token={APIKEY}&q="messi"%20AND%20"Barcelona"&ts=1518472804000&size=100
```

## Aquí podemos identificar:

| Elemento   | Descripción                             |
| :--------- | :-------------------------------------- |
| protocolo  | Puede ser tanto **http** como **https** |
| dominio    | Dirección de la API api.trawlingweb.com |
| parámetros | Parámetros de la consulta               |

## Elementos que especifican la información que se desea y la forma en que se quiere recibir:

| Parámetro | Descripción                                                                                                                                                                                                                                                                                 | Default                                                 | Ejemplo                      |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------------------------------------ | :--------------------------- |
| token     | APIKEY de acceso del cliente al sistema de TrawlingWeb.                                                                                                                                                                                                                                     | Valor obligatorio                                       | ?token={APIKEY}              |
| q         | Expresión construida con palabras o expresiones clave que configura los filtros de búsqueda. Permite hacer combinaciones con los distintos tipos de filtros disponibles mediante los operadores booleanos _y_, _o_ y _no_.                                                                  | Por defecto devuelve todas las publicaciones            | &q="domain=lavanguardia.com" |
| ts        | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos                                                                                                                                                                                                                | Delimita a 3 meses en el pasado a partir de la petición | &ts=1518472804000            |
| tsi       | Se trata del delimitador temporal final. Formato Unix Time en milisegundos                                                                                                                                                                                                                  | Delimita con la fecha de petición                       | &tsi=1524818189854           |
| size      | Cantidad de documentos que se desea recuperar por página. TrawlingWeb fracciona la entrega de datos en bloques de un máximo de 100 documentos. Cada bloque constituye una consulta efectiva. Así este parámetro permite configurar el tamaño de los bloques fijando su valor entre 1 y 100. | 100                                                     | &size=40                     |
| format    | Fija el formato de los archivos de respuesta. Los formatos disponibles són JSON y XML.                                                                                                                                                                                                      | json                                                    | &format=json                 |
| sort      | Orden con el qual se desea recibir los datos de las publicaciones. Estas se puden recibir ordenadas o bien por fecha de publicación (published) o bien por fecha de captura (crawled).                                                                                                      | crawled                                                 | &sort=published              |
| order     | El orden puede ser _asc_ (ascendente) o _desc_ (descendente).                                                                                                                                                                                                                               | asc                                                     | &order=desc                  |

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