# API NEWS & BLOGS - Filtering parameters

The next list shows the available filters that enables to retrieve only the wanted data.

| Filter        | Description                                                                                                                           |
| :------------ | :------------------------------------------------------------------------------------------------------------------------------------ |
| site          | Website from which we want data (or not)                                                                                              |
| domain        | Internet domain from which we want data (or not)                                                                                      |
| title         | Words and expressions that must be present (or not) in the titles of returned publications                                            |
| text          | Words and expressions that must be present (or not) in the body text of returned publications                                         |
| language      | Natural language of the required (or refused) publications. See language codes [ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1)   |
| site_language | Website's language of the required (or refused) publications: en (english), es (spanish), fr (french), ...                            |
| site_country  | Website's country of the required (or refused) publications. See country codes [ISO-3166-2](https://en.wikipedia.org/wiki/ISO_3166-2) |
| site_region   | Website region. See [ISO-3166-2](https://es.wikipedia.org/wiki/ISO_3166-2)                                                            |
| author        | Author of the publication. For example, "Shakespeare"                                                                                 |
| published     | Publishing timestamp in miliseconds. [Conversor](http://www.onlineconversion.com/unix_time.htm)                                       |
| crawled       | Crawling timestamp in miliseconds. [Conversor](http://www.onlineconversion.com/unix_time.htm)                                         |
| site_type     | Type of website: general, news, blog or discussion                                                                                    |

## How to build a filter expression

    q = "(filtro1: valor1) operador (filtro2 : valor2) operador ... (filtroN : valorN__)"

> The spaces between the parts of the expression have been added only in order to gain clarity.

## More information

More information is avaiable in the complete [Lucene's syntax Manual](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

## Scaping special characters

Some characters are part of the query syntax: \+ \- \* && || ! () [] {} ^ " ? ~ : \\ \/

In order to avoid confusions they must be preceded by the "**\\**" character in the query expression. To search (1+1):2 we have to build the querry as it follows: **\\(1\\+1\\)\\:2**.

Let's see another example: to search the URL https://www.linkedin.com we must rewrite as **url:https \:\ / \ / www.linkedin.com**.

## q filters examples

| Example                                                               | Explanation                                                                                                           |
| :-------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
| (site: elpais.com OR site: lavanguardia.com)                          | Retrieve publications from the websites elpais.com or lavanguardia.com or from the both.                              |
| NOT (site:yahoo.com AND site:google.com)                              | Retrieve publications from all the websites excepts from the yahoo.com and google.com websites.                       |
| ((title:rajoy AND (text:España OR text:Morales)) NOT title:españoles) | Retrieve publications where title includes the words "rajoy" and (or "españa" or "morales") and excludes "españoles". |
| (language:es OR language:es)                                          | Retrieve only publications in spanish or french languages.                                                            |
| (site_language:es OR site_language:fr)                                | Retrieve publications from spanish or french websites.                                                                |
| NOT (site_language:es) OR NOT (site_language:fr)                      | Don't retrieve publications from spanish or french websites.                                                          |
| author:Pedrolo                                                        | Retrieve only Manuel de Perolo's publications.                                                                        |
| (site_type:news OR site_type:blogs)                                   | Retrieve publications from news websites or blog websites.                                                            |
| NOT (site_type:news)                                                  | Don't retrieve publication from news websites.                                                                        |
