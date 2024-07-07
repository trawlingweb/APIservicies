# API NEWS & BLOGS - Consultas Booleanas Básicas

En esta sección explicamos a nuestros clientes que las APIs de TrawlingWeb aceptan consultas booleanas combinadas con expresiones de la sintaxis de Lucene. A continuación, mostramos algunos ejemplos prácticos que te ayudarán a tener una mejor experiencia y a optimizar tus búsquedas y resultados.

## Operadores Booleanos esenciales AND, OR y NOT

Las consultas booleanas permiten combinar palabras clave o frases mediante operadores específicos. A continuación, te presentamos los operadores disponibles y algunos ejemplos útiles:

|  Operador   | Uso                                                                                                    |       Ejemplo        |
| :---------: | :----------------------------------------------------------------------------------------------------- | :------------------: |
| x **AND** y | "**x**" e "**y**" aparecerán en los documentos recuperados.                                            | "Mesi" AND "Girona"  |
| x **OR** y  | En los documentos recuperados, aparecerá "**x**", "**y**" o ambos. Se recomienda el uso de paréntesis. | ("Mesi" OR "Girona") |
|  **NOT** x  | No se recuperarán los documentos que incluyan "**x**".                                                 |      NOT "Mesi"      |

### Paréntesis

Utiliza paréntesis para encapsular declaraciones OR y asegurar que los motores de búsqueda ejecuten la consulta correctamente. El operador OR se interpreta como "Me gustaría al menos uno de estos términos."

Por ejemplo: _(Barcelona OR Madrid OR París)_

### Comillas

Las comillas deben utilizarse para buscar frases exactas de más de una palabra. Sin comillas, podrías obtener documentos con las palabras divididas en componentes individuales.

Por ejemplo: _Casa Blanca_

Sin comillas, los resultados podrían incluir páginas que contengan _Casa_ y _Blanca_, pero no necesariamente juntas. Usando comillas, indicas al sistema que solo debe devolver páginas que incluyan la frase exacta en ese orden.

Por ejemplo: _"Casa Blanca"_

### Wildcards

Puedes utilizar un asterisco (\*) para reemplazar algunos caracteres en la construcción de una consulta.

Por ejemplo:

- lavang\* (devolverá lavanguardia)
- \*pais (devolverá elpais)

El asterisco ayuda a crear sentencias largas o a buscar expresiones aunque se desconozca su forma completa.

### Más Información

Para más detalles, consulta el manual completo de sintaxis de Lucene ([aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)), que es la base de nuestro motor de búsqueda.

---

## Sintaxis de Consultas de Lucene

Las APIs de TrawlingWeb permiten realizar consultas que pueden contener operadores booleanos basados en la sintaxis de Lucene, ofreciendo una poderosa herramienta para realizar búsquedas complejas y precisas. La sintaxis de consultas de Lucene está diseñada para ser intuitiva y expresiva. A continuación, te presentamos algunas características clave y ejemplos útiles para optimizar tu experiencia de usuario:

### Otras sintaxis útiles

1.  **Consulta de Término**: Busca un término específico.

    ```
    cocacola
    ```

2.  **Consulta de Frase**: Busca una frase exacta encerrándola entre comillas dobles.

    ```
    "coca cola con gusto a cereza"
    ```

3.  **Consulta con Comodines**: Usa `?` para reemplazar un solo carácter o `*` para reemplazar cero o más caracteres.

    ```
    - ambigu? : (devolveria ambiguO o ambiguA)
    - ejem* : (devolveria entre otros, ejemPLO, ejemPLOS, ejemPLAR, ejemPLIZANTE..etc)
    ```

4.  **Operadores Booleanos**
    Usa `AND`, `OR` y `NOT` para combinar múltiples términos o frases.

        Ejemplos

        AND: Este operador se usa para buscar registros que contengan ambos términos o frases.

        Mcdonalds AND "Burger King"
        
        OR: Este operador se usa para buscar registros que contengan al menos uno de los términos o frases.

        Mcdonalds OR "Burger King"
        
        NOT: Este operador se usa para excluir registros que contengan el término o frase siguiente.

        Mcdonalds AND NOT "Burger King"

        

5. **Consultas Específicas de atributo**: Especifica atributo para buscar en partes particulares del documento.
   ```
   title:ejemplo
   text:"frase exacta"
   ```

### Ejemplso útiles de agrupación de elementos de búsqueda

(...) Usa paréntesis para agrupar cláusulas y formar subconsultas.

```
(coacola OR pepsi) AND (finanzas NOT delito)
```

### Ejemplos de consultas Lucene más utilizadas por nuestros clientes

Aquí tienes algunos ejemplos de consultas para ilustrar el uso de la sintaxis de Lucene en nuestra API de Noticias:

- Búsquedas de Proximidad (o near): Encuentra palabras que estén a cierta distancia entre sí.

   ```
   "delito financiero"~5
   ```
   el match será si se encuentran las dos palabras y estas se encuentra ubicadas a una distancia máxima de 5 caractéres entre estas

- Buscar artículos que contengan la palabra "tecnología":

  ```
  tecnología
  ```

- Buscar artículos con la frase exacta "inteligencia artificial":

  ```
  "inteligencia artificial"
  ```

- Buscar artículos con "clima" en el título y "cambio" en el contenido:

  ```
  title:clima AND contenido:cambio
  ```

- Buscar artículos que mencionen "economía" pero no "recesión":
  ```
  economía NOT recesión
  ```

## Conclusión

Usar la sintaxis de consultas de Lucene con la API de Noticias de TrawlingWeb te permite crear búsquedas precisas y complejas, asegurando que recuperes los datos más relevantes. Para una comprensión más completa de la sintaxis de consultas de Lucene, consulta la [documentación oficial de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

Si tienes alguna pregunta o necesitas más asistencia, por favor contacta a nuestro equipo de soporte.

---

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
- [Correo SAT](mailto:support@trawlingweb.com)
- [Documentación Oficial](https://docs.trawlingweb.com)

**SAC (Soporte administrativo):**
- [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
- [Correo Ventas](mailto:sales@trawlingweb.com)
