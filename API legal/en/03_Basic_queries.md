# Legal API - Basic Boolean Queries

Boolean queries are a type of search that allows combining keywords or even phrases using the operators listed below:

|  Operator   | Usage                                                                                                                   |      Example       |
| :---------: | :---------------------------------------------------------------------------------------------------------------------- | :----------------: |
| x **AND** y | "**x**" and "**y**" will appear in the retrieved documents.                                                             | "Mesi"AND"Girona"  |
| x **OR** y  | In the retrieved documents, either "**x**" or "**y"** or both will appear. It is recommended to use () to avoid errors. | ("Mesi"OR"Girona") |
|  **NOT** x  | Documents that include "**x**" are not retrieved.                                                                       |     NOT"Mesi"      |

## Parentheses

Use parentheses to encapsulate OR statements so that search engines execute the query correctly.

The OR operator is interpreted as "I would like at least one of these terms."

`(Barcelona OR Madrid OR París)`

If you do not enclose all your OR statements in parentheses, your search may work, but it will not work as intended.

## Quotation Marks

Quotation marks should be used when searching for exact phrases of more than one word, or else you may get documents with the phrase split into single-word components.

`Casa Blanca`

Your results could bring back pages that have Casa and Blanca but do not have to appear consecutively.
It behaves like:

`Casa AND Blanca`

However, using quotes around your phrases solves this problem. When you use quotes around a phrase, you are telling the system to only bring back pages that include these search terms in this exact order.

` "Casa Blanca"`

Your search results will now only bring back pages that have all these words in the exact order they are written in.

## Wild Cards

It is possible to use an asterisk (\*) in place of some characters when constructing a query.

```
lavang\*  (devolverá lavanguadia)
\*pais    (devolverá elpais)
```

The asterisk saves time because it helps create longer statements or allows you to search for expressions even if you do not know their complete form.

## More Information

For more information, you can refer to the complete Lucene query syntax manual ( [here](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html) ), which is the basis of our search engine.
