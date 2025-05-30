# API PRINT MEDIA – Consultas Booleanas Básicas

En esta sección te explicamos cómo usar consultas booleanas junto con la sintaxis de Lucene en la API de **Print Media** de TrawlingWeb. Todas las expresiones van dentro del parámetro `q=` en la URL de la petición.

---

## Siempre dentro de `q=`

El parámetro `q=` encapsula **toda** la lógica de búsqueda. Por ejemplo, una llamada completa podría ser:

```
https://api.trawlingweb.com/press-written?
  token=TU_TOKEN
 &q=(site:expreso.com AND title:Corte)
```

---

## Operadores Booleanos esenciales

| Operador | Uso                                                   |           Ejemplo           |
| :------: | :---------------------------------------------------- | :-------------------------: |
| **AND**  | Ambos términos deben aparecer en el artículo.         |   `Corte AND sentencias`    |
|  **OR**  | Al menos uno de los términos debe aparecer.           | `(Corte OR Constitucional)` |
| **NOT**  | Excluye artículos que contengan el término siguiente. |        `NOT tibios`         |

### Paréntesis

Agrupa sub-expresiones para controlar precedencia; muy útil con `OR`:

```
(site:expreso.com OR site:comercio.com)
```

### Comillas

Encuentra frases exactas de más de una palabra:

```
"title:Corte Constitucional"
```

Sin comillas, Lucene buscará cada término por separado.

### Wildcards

Reemplaza caracteres con:

- `*` → Cero o más caracteres
- `?` → Exactamente un carácter

Por ejemplo:

```
site:diario-*
text:constitucion?
```

---

## Ejemplos de consultas en `q=`

| Ejemplo                                                | Explicación                                                                     |
| :----------------------------------------------------- | :------------------------------------------------------------------------------ |
| `(site:expreso.com OR site:comercio.com)`              | Artículos de Expreso o El Comercio.                                             |
| `NOT (site:lavanguardia.com OR site:elpais.com)`       | Todos excepto los de La Vanguardia y El País.                                   |
| `((title:Corte AND text:sentencias) NOT title:tibios)` | Título con “Corte” y cuerpo con “sentencias”, excluyendo “tibios” en el título. |
| `(language:es OR language:en)`                         | Solo artículos en español o inglés.                                             |
| `site_country:ec AND site_language:es`                 | Medios de Ecuador cuyo idioma es español.                                       |
| `author:Romero`                                        | Artículos cuyo autor contenga “Romero”.                                         |
| `site_type:Magazine`                                   | Solo artículos de medios clasificados como “Magazine”.                          |

---

## Sintaxis avanzada de Lucene

1. **Término simple**

   ```
   futbol
   ```

2. **Frase exacta**

   ```
   "partido de futbol"
   ```

3. **Proximidad**

   ```
   "Corte Constitucional"~5
   ```

   → “Corte” y “Constitucional” con máximo 5 palabras de separación.

4. **Campo específico**

   ```
   title:reforma AND text:educacion
   ```

5. **Negación avanzada**

   ```
   text:política AND NOT title:gobierno
   ```

Para más detalles de la sintaxis de Lucene, consulta la [documentación oficial](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

---

# Contacto

Si necesitas ayuda o deseas ampliar tu plan:

- **Soporte Técnico (SAT):** [support@trawlingweb.com](mailto:support@trawlingweb.com)
- **Soporte Administrativo (SAC):** [gestion@trawlingweb.com](mailto:gestion@trawlingweb.com)
- **Ventas (Sales):** [marketing@trawlingweb.com](mailto:marketing@trawlingweb.com)
