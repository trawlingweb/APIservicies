# API Twitter - Acceso al servicio

## Registro de usuario

Para poder acceder al servicio primero hay que estar registrado en nuestra base de datos.

Una vez registrado, el visitante recibe el rol de usuario de pruebas. Este rol permite acceder a la zona de clientes y realizar una cierta cantidad de configuraciones de Workers gratuitas.

## Contratación de servicios

Agotado el periodo de prueba, el usuario que desee continuar usando el servicio o ampliar el mismo deberá formalizar un contrato. TrawlingWeb permite escoger entre varios bloques de contratación, con diferente cantidad de Workers cada uno. De esta manera el cliente podrá escoger el bloque que se adapte mejor a sus necesidades.

## Modos de acceso

Se puede acceder al servico de dos maneras: a través de la API para sistemas en producción y a través de la consola para realizar pruebas.

### Acceso por API

El sistema de TrawlinWeb dispone de una interfície API REST. Se trata de un mòdulo que permite el acceso remoto desde un sistema cliente. El programa del usuario accede al sistema de TrawlingWeb y realiza consultas automatizadas a los Workers.

Estas consultas automatizadas se realizan con un lenguaje de consultas propio que tiene su propia sintaxis. Recomendamos leer atentamente esta documentación para evitar la construcción de consultas erróneas.
