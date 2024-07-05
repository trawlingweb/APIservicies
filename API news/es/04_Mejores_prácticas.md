# API NEWS & BLOGS - Mejores prácticas y consejos

Con el fin de utilizar la API es necesario llamar a una URL de punto final con su token de acceso privado. Puede generar la URL de su llamada en nuestro Testeador visual de la API (que debe acceder a https://dashboard.trawlingweb.com/playground).

## Integridad de los datos

Cada solicitud al API puede devolver un máximo de 100 mensajes coincidentes con su consulta. Sin embargo, pueden haber muchos más resultados que coincidan con sus parámetros de filtro. Para consumir todos los datos ha de seguir realizando llamadas a la URL indicada en el parámetro **next** de las salida de cada solicitud.

## Ejemplo de salida

```
requestLeft	9999999
totalResults	295404987
restResults	295404887
next	"http://api.trawlingweb.com/?token=0000000000000000000000000000&q=language%3Aen&ts=1517443760316&tsi=1524818189854"
}
```

## Paginación

Dependiendo del orden de clasificación que desea y el orden de los resultados, la dirección URL "next" incluye los valores &ts y &tsi con un conportamiento adaptado a la forma de la forma de ordenar los resultados. Tanto $ts como $tsi son marcas de tiempo (UnixMicrotime)

## Modos de paginación

Estos son los 4 modos de funcionamiento de la paginación.

#### &order=**crawled** &sord=**asc**$size=100 _(Modo por defecto)_

Las noticias ordenadas por fecha de captura (crawled) de viejas a nuevas. El el "next" el $ts salta de 100 resultados hasta llegar a $tsi

#### &order=**crawled**&sord=**desc**$size=100

Las noticias ordenadas por fecha de captura (crawled) de nuevas a viejas. El el "next" el $tsi salta de 100 resultados hasta llegar a $ts

#### &order=**published**&sord=**asc**$size=100

Las noticias ordenadas por fecha de publicación (published) de viejas a nuevas. El el "next" el $ts salta de 100 resultados hasta llegar a $tsi

#### &order=**published**&sord=**desc**$size=100

Las noticias ordenadas por fecha de publicación (published) de nuevas a viejas. El el "next" el $tsi salta de 100 resultados hasta llegar a $ts

## Mantenimiento Periódico de Fuentes de Medios

El mantenimiento periódico de las fuentes de medios es constante y core en TrawlingWeb e implica una reevaluación integral de cada fuente, lo que a menudo conlleva la incorporación de nuevas secciones para raspar contenido no capturado anteriormente. Contar con las fechas de captura (`crawled`) y publicación (`published`) permite gestionar estas actualizaciones de manera eficiente.

Al agregar nuevas fuentes de medios a nuestra cobertura, frecuentemente incluimos su historial realizando un raspado inicial profundo de todas sus secciones. Nuevamente, las fechas de captura (`crawled`) y publicación (`published`) facilitan este proceso.

Ciertas secciones de los medios, además del contenido cronológico, muestran contenido no cronológico (como rankings o noticias relacionadas) que también capturamos.

### Consideraciones

- **Frecuencia de Raspado**: La frecuencia de raspado de una fuente de medios se determina por las necesidades del cliente, los requisitos funcionales, la cantidad de noticias y la frecuencia de publicación del medio.
- **Diferenciación de Fechas**: Diferenciar claramente la fecha de captura (`crawled`) de la fecha de publicación (`published`) permite que los clientes decidan qué noticias incorporar.
- **Filosofía de Entrega de Contenido**: Nuestra filosofía es entregar todas las noticias capturadas, dejando la decisión sobre cómo utilizar este contenido a los clientes.

### Noticias Entregadas y Descartadas

- **Noticias Entregadas**: Todas las noticias capturadas se entregan al cliente.
- **Noticias Descartadas**: Los clientes tienen la opción de descartar noticias según sus criterios y necesidades específicas.


## Consejos sobre el Uso de las Fechas `published` y `crawled`

Trawlingweb entrega dos fechas para cada noticia: `published` (fecha de publicación) y `crawled` (fecha de captura). Esto es crucial ya que, al incorporar nuevas secciones, el sistema puede detectar como nuevas noticias que fueron publicadas días o incluso meses atrás.

También puede suceder que los medios modifiquen sus sistemas de publicación, lo que puede provocar la aparición de noticias antiguas debido a errores o estrategias de SEO. 
Para evitar o controlar estos sucesos, aconsejamos que los clientes implementen reglas de seguridad en sus sistemas.

### Consejos sobre reglas par garantizar el buen uso de las fechas:

- **Filtros de Fecha**: Establecer filtros para ignorar noticias con fechas de publicación muy antiguas.
- **Reglas de Relevancia**: Crear criterios que determinen la relevancia de las noticias en función de su fecha de publicación y la fecha de captura.
- **Monitoreo de Cambios**: Supervisar los cambios en los sistemas de publicación de los medios para ajustar las reglas de captura y procesamiento en consecuencia.
- **Alertas y Notificaciones**: Configurar alertas para detectar y notificar la aparición de noticias antiguas, permitiendo una revisión manual si es necesario.

Implementar estas medidas ayuda a nuestros clientes a mantener la integridad y relevancia de los datos capturados por TrawlingWeb.


