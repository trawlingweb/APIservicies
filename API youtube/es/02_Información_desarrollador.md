# API YOUTUBE - Cosas que cada desarrollador debería saber

## API REST

Trawlingweb.com es una API REST, por lo que aunque los datos está destinado a ser consumido como un flujo de datos, es necesario llamar a la API de forma continua con el fin de recibir los lotes de datos.


## Estructura de URL


### La llamada de consulta URL tiene tres partes:

- Autentificación
- El HTTP GET cadena de parámetros para la autenticación, período temporal.
- La cadena de consulta de filtro y emparejamientos de valor buscados lo que la API recupera sólo los datos que necesita.



## La autenticación

La autenticación se confirmó a través de un token de acceso única aprobada en la URL llamada a la API. Puede encontrar su token de acceso en el panel de control.



## Límite de tarifa

Todos los planes de API YOUTUBE incluyen un único token de acceso único, con una limitación de velocidad incorporados de 1 (un) solicitud cada 5 segundos. Para superar dicho límite se tendrá que solucitar especificamente.



## Formatos de salida

Proporcionamos los datos en el siguiente formato de salida:

| Formato | Descripción |
|-----------------|:---------------------------------------------|
| JSON  |  JavaScript Object Notation |



## API de soporte de seguridad HTTP / HTTPS

Twalingwerb.com soporta tanto las llamadas de punto final HTTP y HTTPS (SSL).



## Las peticiones GET

Puede llamar a la API mediante peticiones GET. Si realiza llamadas muy largas a la API dividela en varias consultas más cortas.



## Códigos de estado HTTP
| Código         | Descripción   |
| ------------- |:---------------|
| 200 | ¡Éxito! |
| 401 | Usuario no autorizado o sin tokens disponibles |
| 404 | Error de sintaxis |
| 500 | No se pudo ejecutar la consulta |
| 503 | Servicio no disponible temporalmente |
| 429 | Excede el límite de velocidad |

NOTA: Detalle del error explicado en el retorno de la request.