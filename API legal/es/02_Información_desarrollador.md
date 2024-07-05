# API Legal - Cosas que cada desarrollador debería saber

## API REST

Trawlingweb.com API Legal es una API REST, por lo que aunque los datos está destinado a ser consumido como un flujo de datos, es necesario llamar a la API de forma continua con el fin de recibir lotes de datos.

## Estructura de URL

### La llamada de consulta URL tiene tres partes:

- Autentificación
- El HTTP GET cadena de parámetros para la autenticación, período de tiempo, la paginación, y el formato.
- La cadena de consulta que pasa las llaves de filtro y emparejamientos de valor respectivos lo que la API recupera sólo los datos que necesita.

## La autenticación

La autenticación se confirmó a través de un token de acceso única aprobada en la URL llamada a la API. Puede encontrar su token de acceso en el panel de control.

## Los formatos de salida

Proporcionamos los datos en formato estructurado:

| Formato | Descripción                |
| ------- | :------------------------- |
| JSON    | JavaScript Object Notation |

## API de soporte de seguridad HTTP / HTTPS

Twalingwerb.com soporta tanto las llamadas de punto final HTTP y HTTPS (SSL).

## Las peticiones GET

Puede llamar a la API mediante peticiones GET. Si realiza llamadas muy largas a la API dividela en varias consultas más cortas. El límite operativo de una llamada GET es de 4000 carácteres en total.

## Códigos de estado HTTP

| Código | Descripción                                    |
| ------ | :--------------------------------------------- |
| 200    | ¡Éxito!                                        |
| 401    | Usuario no autorizado o sin tokens disponibles |
| 404    | Error de sintaxis                              |
| 500    | No se pudo ejecutar la consulta                |
| 503    | Servicio no disponible temporalmente           |

NOTA: Detalle del error explicado en el retorno de la request.
