# API Facebook - Método GET /delete

Si un Worker ya no te sirve, puedes borrarlo y dejar espacio para crear uno nuevo.

# Parámetros GET

Veamos la estructura de la consulta de ejemplo:

````
https://facebook.trawlingweb.com/delete/{WORKERID}?token={APIKEY}
````
## Parámetros PATH:

| Elemento | Descripción | Default | Ejemplo | 
|:---------|:------------|:-------|:-----------|
| protocolo | Puede ser tanto **http** como **https**                  |
| dominio | Dirección de la API Facebook.trawlingweb.com |
| método | delete |
| workerid | WORKERID de acceso a la basedetados del worker en el sistema de TrawlingWeb. | Valor obligatorio | /{WORKERID}?

## Parámetros QUERY:

| Parámetro | Descripción  | Default | Ejemplo | 
|:----------|:-------------|:-------|:-----------|
| token | APIKEY de acceso del cliente al sistema de TrawlingWeb .| Valor obligatorio |  ?token={APIKEY}

# Respuesta de salida - RESPONSE

Una vez lanzada una petición al API de Facebook éste devolverá una respuesta estructurada de la siguiente forma: 

##  Status 200 - Datos de la retorno

| Campo | Descripción |  Tipo | 
|-------------|--------|:--------:|:---------:|
| worker | Identificador del Worker creado. | Cadena |
| msg | Descripción indicando acción exitosa | Cadena | 

## Ejemplo de respuesta en formato json:

````json
"response" : {
    "worker" : "...",
    "msg" : "..."
}
````

##  Status 400 - Datos de la retorno

| Campo | Descripción |  Tipo |
|-------------|--------|:--------:|
| error | Descripción del error | Cadena |

## Ejemplo de respuesta en formato json:

````json
"response" : {
    "error" : "..."
}
````

# Características de los Workers

Cada Worker almacena los resultados durante 30 días.

El usuario puede eliminar un Worker concreto. Esta eliminación implica la destrucción tanto de la configuración del mismo como la base de datos asociada a el.

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
- [Correo SAT](mailto:support@trawlingweb.com)
- [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
- [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
- [Correo Ventas](mailto:sales@trawlingweb.com)

