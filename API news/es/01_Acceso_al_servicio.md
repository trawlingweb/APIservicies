# API NEWS & BLOGS - Acceso al servicio

## Registro de usuario

Para poder acceder al servicio primero hay que estar registrado en nuestra base de datos.

Una vez registrado, el visitante recibe el rol de usuario de pruebas. Este rol permite acceder a la zona de clientes y realizar una cierta cantidad de consultas gratuitas.

## Contratación de servicios

Agotadas las consultas gratuitas, el usuario que desee continuar usando el servicio deberá formalizar un contrato. TrawlingWeb permite escoger entre varios bloques de contratación, con diferente cantidad de consultas cada uno. De esta manera el cliente podrá escoger el bloque que se adapte mejor a sus necesidades.

## Modos de acceso

Se puede acceder al servico de dos maneras: a través de la API para sistemas en producción y a través de la consola para realizar pruebas.

### Acceso por API

El sistema de TrawlinWeb dispone de una interfície API REST. Se trata de un mòdulo que permite el acceso remoto desde un sistema cliente. El programa del usuario accede al sistema de TrawlingWeb y realiza consultas automatizadas. A su vez recibe mensajes con la información requerida y otros datos relativos al servicio como, por ejemplo, el número de consultas disponibles.

Estas consultas automatizadas se realizan con un lenguaje de consultas propio que tiene su propia sintaxis. Recomendamos leer atentamente esta documentación para evitar la construcción de consultas erróneas.

### Acceso por consola

Al mismo tienpo el sitio web de TrawlingWeb dispone de una consola de consultas para facilitar al usuario de pruebas una demostración del funcionamiento del servicio. Permite construir la consulta con el mismo lenguaje utilizado para realizar consultas a la API. Por eso recomendamos que antes de acceder a la API, se realizen pruebas en la consola. Permite familiarizarse con todos los parámetros de búsqueda disponibles y aprender a configurar los filtros para recuperar los datos deseados.
