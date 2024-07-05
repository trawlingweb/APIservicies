# API Legal - Mejores prácticas

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado.

## Integridad de los datos

Cada solicitud al API puede devolver un máximo de 100 mensajes coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados que coincidan con sus parámetros de filtro. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
restResults	295404887
next	"http://law.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&q=Europa&ts=1517443760316&tsi=1524818189854"
}
```

## Paginación

Dependiendo del número total de resultados (totalResults) la API establecerá automaticamente que marcas de tiempo son necesarias para que en la url de next se incluyan los siguientes resultados. Tanto \$ts como \$tsi son marcas de tiempo (UnixMicrotime)
