# API Legal - Consultas boleanas básicas

Las cosultas boleanas on un tipo de búsqueda que permiten combinar palabras clave, o incluso frases, mediante los operadores de la lista que sigue a continuación:

|  Operador   | Uso                                                                                                                                               |      Ejemplo       |
| :---------: | :------------------------------------------------------------------------------------------------------------------------------------------------ | :----------------: |
| x **AND** y | "**x**" e "**y**" aparecerán en los documentos recuperados.                                                                                       | "Mesi"AND"Girona"  |
| x **OR** y  | en los documentos recuperados, o bien aparecerá "**x**", o bien aparecerà "**y**" o bien las dos. Se recomienda el uso de () para evitar errores. | ("Mesi"OR"Girona") |
|  **NOT** x  | No se recuperan los documentos que incluyen "**x**"                                                                                               |     NOT"Mesi"      |

## Los paréntesis

Utilice paréntesis para encapsular declaraciones OR para que los motores de búsqueda ejecuten la consulta de forma correcta.

El operador OR se interpreta como "Me gustaría al menos uno de estos términos."

`(Barcelona OR Madrid OR París)`

Si no adjunta todas sus declaraciones OR entre paréntesis, su búsqueda puede funcionar pero no va a funcionar según lo previsto.

## Comillas

Las comillas se deben utilizar en la búsqueda de frases exactas de más de una palabra, o de lo contrario pueden obtener documentos con la frase dividido en componentes de una sola palabra.

`Casa Blanca`

Sus resultados podrían traer de vuelta las páginas que tienen _Casa_ y _Blanca_ pero no tienen que aparecer de forma consecutiva.
Se comporta como

`Casa AND Blanca`

Sin embargo, el uso de comillas alrededor de sus frases soluciona este problema. Cuando se utiliza comillas alrededor de una frase, le está diciendo al sistema sólo para traer de vuelta las páginas que incluyen estos términos de búsqueda en este orden exacto.

` "Casa Blanca"`

Resultado de su búsqueda ahora sólo traer de vuelta las páginas que tienen todas estas palabras en el orden exacto que se hayan escrito en.

## Wild Cards

Es posible utilizar un asterisco (\*) en lugar de algunos caracteres en la costrucción de una consulta.

```
lavang\*  (devolverá lavanguadia)
\*pais    (devolverá elpais)
```

El asterisco permite ahorrar tiempo porque ayuda a crear sentencias largas o permite buscar expresiones aunque se desconozca su forma completa.

## Más información

Para más información puede consultar el manual completo de syntaxis de Lucene ( [aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html) ) siendo esta nuestra base de motor de búsqueda.
