# API Print media – Parámetros GET

### Introducción

En esta sección encontrarás cómo construir y ejecutar consultas a la API de **Print media** de TrawlingWeb. Mediante parámetros GET podrás filtrar y recuperar artículos de prensa escrita según tus necesidades: medio, fecha, paginación, formato, orden, etc.

A continuación se muestra la estructura de ejemplo, el desglose de cada componente y una tabla con la descripción, valor por defecto y ejemplos prácticos de todos los parámetros disponibles.

---

## Método estándar

```
https://api.trawlingweb.com/press-written?
   token={APIKEY}
 & from=2025-05-01
 & to=2025-05-29
 & page=1
 & size=50
 & site=Expreso
 & site_country=ec
 & sort=published
 & order=desc
 & format=json
```

---

## Componentes de la URL

| Elemento       | Descripción                                             |
| :------------- | :------------------------------------------------------ |
| **protocolo**  | `http` o `https`                                        |
| **dominio**    | `api.trawlingweb.com`                                   |
| **endpoint**   | `/press-written`                                        |
| **parámetros** | Cadena de pares `clave=valor` tras `?` separada por `&` |

---

## Parámetros GET

| Parámetro      | Descripción                                                            | Default              | Ejemplo               |
| :------------- | :--------------------------------------------------------------------- | :------------------- | :-------------------- |
| `token`        | Tu clave de acceso única a TrawlingWeb. Obligatorio en cada llamada.   | —                    | `token=YOUR_API_KEY`  |
| `from`         | Fecha inicial de publicación de los artículos (ISO 8601).              | 3 meses atrás        | `from=2025-05-01`     |
| `to`           | Fecha final de publicación de los artículos (ISO 8601).                | Fecha de la petición | `to=2025-05-29`       |
| `page`         | Número de página de resultados (paginación).                           | 1                    | `page=2`              |
| `size`         | Artículos por página (1–100).                                          | 100                  | `size=50`             |
| `site`         | Nombre del medio (tal como `"Expreso"`, `"El Comercio"`, etc.).        | Todos                | `site=Expreso`        |
| `site_country` | Código ISO 3166-1 alpha-2 del país del medio (p.ej. `ec`, `es`, `co`). | Todos                | `site_country=ec`     |
| `site_type`    | Tipo de medio (p.ej. `Newspaper`, `Magazine`).                         | Todos                | `site_type=Newspaper` |
| `site_topic`   | Tema principal del medio (p.ej. `News`, `Economy`, `Sports`).          | Todos                | `site_topic=News`     |
| `sort`         | Campo por el que ordenar resultados: `published` o `crawled`.          | `crawled`            | `sort=published`      |
| `order`        | Dirección de orden: `asc` (ascendente) o `desc` (descendente).         | `asc`                | `order=desc`          |
| `format`       | Formato de la respuesta: `json` o `xml`.                               | `json`               | `format=xml`          |

---

### Ejemplo completo

```
https://api.trawlingweb.com/press-written?
   token=ABC123XYZ
 & from=2025-05-01
 & to=2025-05-29
 & page=1
 & size=50
 & site=Expreso
 & site_country=ec
 & sort=published
 & order=desc
 & format=json
```

Con esta consulta recuperarás hasta 50 artículos de “Expreso” publicados entre el 1 y el 29 de mayo de 2025, ordenados por fecha de publicación de más reciente a más antigua, en formato JSON.

---

# Contacto

Si tienes preguntas, necesitas asistencia o quieres ampliar tu plan, escríbenos a:

**Soporte Técnico (SAT):** [support@trawlingweb.com](mailto:support@trawlingweb.com)
**Soporte Administrativo (SAC):** [gestion@trawlingweb.com](mailto:gestion@trawlingweb.com)
**Ventas (Sales):** [marketing@trawlingweb.com](mailto:marketing@trawlingweb.com)
