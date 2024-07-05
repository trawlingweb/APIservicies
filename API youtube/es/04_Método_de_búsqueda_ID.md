# API Youtube - Método GET /search_ids

Permite realitzar búsquedas en Youtube para obtener vídeos usando diferentes operadores para así acotar el contenido.

El contenido devuelto es el ID de cada video sin datos descriptivos, estadísticas y comentarios.



# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

````
https://youtube.trawlingweb.com/search_ids/?token={APIKEY}&q=messi&tsi=15350188800000&ts=1547510400000&size=50
````

## Parámetros PATH

| Elemento | Descripción |
|:---------|:-------------|
| protocolo | Puede ser tanto **http** como **https** |
| dominio | Dirección de la API youtube.trawlingweb.com |
| método | Método usado SEARCH_IDS |
| parámetros | Parámetros de la consulta |

## Parámetros QUERY

| Parámetro | Descripción  |Default |Ejemplo    | 
|:----------|:-------------|:-------|:-----------|
| token | APIKEY de acceso del cliente al sistema de TrawlingWeb.| Valor obligatorio |  ?token={APIKEY}
| q | Expresión construida con palabras o expresiones clave que configura los filtros de búsqueda. Permite hacer combinaciones con los distintos tipos de filtros disponibles por Youtube| Elemento obligatorio| &q=messi|
| ts | Se trata del delimitador temporal inicial. Formato Unix Time en milisegundos | Delimita a 3 meses en el pasado a partir de la petición| &ts=1518472804000|
| tsi | Se trata del delimitador temporal final. Formato Unix Time en milisegundos | Delimita con la fecha de petición | &tsi=1524818189854|
| size | Cantidad de vídeos que se desea recuperar por página. TrawlingWeb fracciona la entrega de datos en bloques de un máximo de 50 documentos. Cada bloque constituye una consulta efectiva. Así este parámetro permite configurar el tamaño de los bloques fijando su valor entre 1 y 50.|50| &size=50|


# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API, éste devolverá los datos estructurados en función del método de obtención: 


## Datos de búsqueda de ids de vídeos

| Campo | descripción | Tipo | Formato |
| ------- | ---------|:--------:|:---------:|
| id | ID que YouTube utiliza para identificar de forma exclusiva el vídeo. | Cadena | Cadena alfanumérica |


## Datos de petición

| Campo | Descripción | Tipo |
|:-----|:------|:--------:|
| requestLeft | Total de consultas pendientes de la subscripción| Entero |
| totalResults | Total aproximado de resultados encontrados por la consulta | Entero |
| pageResults | Número de vídeos listados | Entero |
| next | URL para continuar con la paginación y así obtener todos los resultados | Cadena |


## Ejemplo de respuesta en formato json:


````json
"response" : {
  "data" : [{
    "id" : "..."
  }],
  "requestLeft" : "...",
  "totalResults" : "...",
  "restResults" : "...",
  "next" : "..."
}
````

# API YOUTUBE - Consultas básicas

El API permite las mismas consultas que se realizan al actual buscador de la web de Youtube. Los criterios en que se aplican al filtrar los vídeos son establedos por la propia Youtube.

## Booleanas

|  Operador   | Uso                                                                                                                                               |      Ejemplo       |
|:-----------:|:--------------------------------------------------------------------------------------------------------------------------------------------------|:------------------:|
| __AND__ | El operador __AND__ es un operador implícito al incluir varios términos con espacio. aparecerán en los vídeos recuperados. También se puede usar el símbolo __+__                                                                                     | "Messi" "Girona"  |
| __OR__ | El operador __OR__ se estable con __\|__ . Los vídeos recuperados, o bien aparecerá "__x__", o bien aparecerà "__y__" o bien las dos. Se recomienda el uso de __()__ para evitar errores. | ("Messi"\|"Girona") |
|  __NOT__  | El operador __NOT__ se establece con __-__ . No se recuperan los documentos que incluyen "__x__"                                                                                               |     -Messi      |


## Los paréntesis

Utilice paréntesis para encapsular declaraciones OR para que los motores de búsqueda ejecuten la consulta de forma correcta.

Por ejemplo: *(Barcelona|Madrid|París)*


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

### Búsqueda de vídeos por duración múnima de 20 minutos
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

### Búsqueda de vídeos convinado los anteriores
	(Barcelona AND Paris) -messi ,4k , long


# API YOUTUBE - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado. Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/playground).



## Integridad de los datos

Cada solicitud al API puede devolver un número máximo de elementos coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados que coincidan con sus parámetros de filtro. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.



## Ejemplo de salida

````
requestLeft	9999999
totalResults	295404987
next	"http://youtube.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&q=messi"
}
````



## Paginación

Al realizar peticiones a los métodos SEACH_IDS estos devuelven un máximo de 50 vídeos. Se habilita una url de next para continuar con la obtención de vídeos si estos superan dicha cantidad.