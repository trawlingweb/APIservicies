# Uso de Consultas Booleanas Básicas en el API de API TikTok de TrawlingWeb

Las APIs de TrawlingWeb aceptan consultas booleanas combinadas con expresiones de la sintaxis de Lucene. A continuación, mostramos algunos ejemplos prácticos que te ayudarán a tener una mejor experiencia y optimizar tus búsquedas y resultados al utilizar la API de API TikTok.

Recuerda que estas expresiones booleanas solo pueden utilizarse dentro del parámetro q= en la llamada a la API y deben combinarse con los filtros y parámetros PATH necesarios.

## Siempre dentro de `q=`
Las consultas booleanas o los parámetros de sintaxis de Lucene siempre deben utilizarse dentro del parámetro q= en la estructura de la URL de llamada a la API. Los elementos dentro de q= constituyen toda la consulta que se adjunta a la llamada a la API.

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

# Uso de Sintaxis de Consultas de Lucene

Las APIs de TrawlingWeb permiten realizar consultas que pueden contener operadores booleanos combinados con expresiones de la sintaxis de Lucene, ofreciendo una poderosa herramienta para realizar búsquedas complejas y precisas. La sintaxis de consultas de Lucene está diseñada para ser intuitiva y expresiva. 

A continuación, te presentamos algunas características clave y ejemplos útiles para optimizar tu experiencia de usuario:


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
    
    - ejem* : (devolveria, entre otros, resulatdos que contegan palabras como, ejemPLO, ejemPLOS, ejemPLAR, ejemPLIZANTE..etc)
    
    - *finanzas : (devolveria, entre otros, resulatdos que contegan palabras como, "microfinanzas", "finanzas", "macrofinanzas", etc.)
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
   text:"frase exacta"
   region:mx
   language:es
   ```

   ***Recuerda que: Las consultas booleanas o los parámetros de sintaxis de Lucene siempre deben utilizarse dentro del parámetro q= en la estructura de la URL de llamada a la API. Los elementos dentro de q= constituyen toda la consulta que se adjunta a la llamada a la API.***

### Campos filtrables disponibles

Cuando escribes `campo:valor` dentro de `q=`, puedes acotar la búsqueda a un atributo concreto del documento. Los campos disponibles en el índice de TikTok son los siguientes:

#### Campos de texto (búsqueda por defecto)

Estos son los campos donde se buscan las palabras clave cuando no antepones ningún atributo. También puedes referenciarlos explícitamente con `campo:valor`.

| Campo             | Descripción                                            |
| :---------------- | :----------------------------------------------------- |
| `text`            | Texto/descripción del post                             |
| `user_name`       | Nombre del creador                                     |
| `user_screen_name`| Nombre de usuario mostrado (handle)                    |
| `user_id_name`    | Identificador interno del usuario                      |
| `music_title`     | Título de la música/audio asociado al post             |
| `user_signature`  | Bio del perfil del creador                             |

#### Campos de localización e idioma (ISO 3166-1 / ISO 639-1, siempre en **minúsculas**)

| Campo             | Descripción                                                     | Ejemplos            |
| :---------------- | :-------------------------------------------------------------- | :------------------ |
| `region`          | País asociado a la publicación                                  | `mx`, `es`, `ar`, `co`, `us` |
| `user_region`     | País declarado en el perfil del creador                         | idem                |
| `language`        | Idioma detectado del contenido del post                         | `es`, `en`, `pt`, `un` (indefinido) |
| `user_language`   | Idioma del perfil del creador                                   | idem                |

### Ejemplos combinando keywords con región e idioma

```
q=(coca cola OR pepsi) AND region:mx AND language:es
q=elecciones AND (region:mx OR region:co OR region:ar) AND language:es
q=marca AND user_region:mx AND language:es
q=fútbol AND region:es AND NOT language:un
```

> **Nota importante sobre la fiabilidad de `region` y `language`:** estos valores provienen directamente del propio TikTok — nosotros los entregamos tal cual los recibimos, sin recalcularlos ni validarlos. TikTok no siempre etiqueta con precisión: es habitual encontrar posts marcados con un país (por ejemplo `region:uy`) que en realidad son de otro (`mx`), o contenido claramente en español que aparece con `language:en` o `language:un` porque el detector se equivoca con textos cortos, hashtags o emojis. Úsalos como filtro para reducir ruido y acotar volumen, pero no como verdad absoluta; si necesitas cobertura exhaustiva de un mercado combínalos con keywords locales, hashtags característicos o varias regiones a la vez (`region:mx OR user_region:mx`).

### Ejemplso útiles de agrupación de elementos de búsqueda

(...) Usa paréntesis para agrupar cláusulas y formar subconsultas.

```
(coacola OR pepsi) AND (finanzas NOT delito)
```

### Ejemplos de consultas Lucene más utilizadas por nuestros clientes

Aquí tienes algunos ejemplos de consultas para ilustrar el uso de la sintaxis de Lucene en nuestra API de Noticias:

* Buscar artículos que contengan la palabra "tecnología":

  ```
  tecnología
  ```

* Buscar artículos con la frase exacta "inteligencia artificial":

  ```
  "inteligencia artificial"
  ```

* Buscar artículos con "clima" en el título y "cambio" en el contenido:

  ```
  title:cambio AND text:clima
  ```

* Buscar artículos que mencionen "economía" pero no "recesión":
  ```
  economía NOT recesión
  ```

### Más Información

Para más detalles, consulta el manual completo de sintaxis de Lucene ([aquí](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)), que es la base de nuestro motor de búsqueda.

## Conclusión y más Información

Usar la sintaxis de consultas de Lucene con la API de Noticias de TrawlingWeb te permite crear búsquedas precisas y complejas, asegurando que recuperes los datos más relevantes. Para una comprensión más completa de la sintaxis de consultas de Lucene, consulta la [documentación oficial de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

Si tienes alguna pregunta o necesitas más asistencia, por favor contacta a nuestro equipo de soporte.

---

# Contacto
Si tienes alguna pregunta, necesitas asistencia, contratar o ampliar tus servicios por favor contacta con nosotros.

**SAT (Soporte Técnico):**
* [Correo SAT](mailto:support@trawlingweb.com)
* [Documentación Oficial](https://github.com/trawlingweb/APIservicies/tree/main/API%20TikTok)

**SAC (Soporte administrativo):**
* [Correo SAC](mailto:gestion@trawlingweb.com)

**Sales (Soporte ventas):**
* [Correo Ventas](mailto:sales@trawlingweb.com)