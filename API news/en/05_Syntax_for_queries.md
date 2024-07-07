## API NEWS & BLOGS - Basic Boolean Queries

In this section, we explain to our customers that the TrawlingWeb APIs accept boolean queries combined with Lucene syntax expressions. Below, we show some practical examples to help you have a better experience and optimize your searches and results.

## Essential Boolean Operators AND, OR, and NOT

Boolean queries allow you to combine keywords or phrases using specific operators. Below are the available operators and some useful examples:

|  Operator   | Usage                                                                                                    |       Example        |
| :---------: | :----------------------------------------------------------------------------------------------------- | :------------------: |
| x **AND** y | "**x**" and "**y**" will appear in the retrieved documents.                                            | "Mesi" AND "Girona"  |
| x **OR** y  | In the retrieved documents, "**x**", "**y**" or both will appear. Parentheses are recommended. | ("Mesi" OR "Girona") |
|  **NOT** x  | Documents that include "**x**" will not be retrieved.                                                 |      NOT "Mesi"      |

### Parentheses

Use parentheses to encapsulate OR statements and ensure search engines execute the query correctly. The OR operator is interpreted as "I would like at least one of these terms."

For example: _(Barcelona OR Madrid OR Paris)_

### Quotes

Quotes should be used to search for exact phrases of more than one word. Without quotes, you might get documents with the words split into individual components.

For example: _White House_

Without quotes, the results could include pages that contain _White_ and _House_, but not necessarily together. Using quotes, you indicate to the system that it should only return pages that include the exact phrase in that order.

For example: _"White House"_

### Wildcards

You can use an asterisk (\*) to replace some characters in constructing a query.

For example:

- lavang\* (will return lavanguardia)
- \*pais (will return elpais)

The asterisk helps to create long sentences or to search for expressions even if their complete form is unknown.

### More Information

For more details, check the complete Lucene syntax manual ([here](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)), which is the basis of our search engine.

---

## Lucene Query Syntax

The TrawlingWeb APIs allow queries that can contain boolean operators based on Lucene syntax, offering a powerful tool for conducting complex and precise searches. Lucene's query syntax is designed to be intuitive and expressive. Below are some key features and useful examples to optimize your user experience:

### Other Useful Syntax

1.  **Term Query**: Searches for a specific term.

    ```
    cocacola
    ```

2.  **Phrase Query**: Searches for an exact phrase enclosed in double quotes.

    ```
    "cherry flavored coca cola"
    ```

3.  **Wildcard Query**: Use `?` to replace a single character or `*` to replace zero or more characters.

    ```
    - ambigu? : (would return ambiguous or ambigua)
    - exam* : (would return, among others, example, examples, exemplary, exemplifying..etc)
    ```

4.  **Boolean Operators**
    Use `AND`, `OR`, and `NOT` to combine multiple terms or phrases.

        Examples

        AND: This operator is used to search for records that contain both terms or phrases.

        Mcdonalds AND "Burger King"
        
        OR: This operator is used to search for records that contain at least one of the terms or phrases.

        Mcdonalds OR "Burger King"
        
        NOT: This operator is used to exclude records that contain the next term or phrase.

        Mcdonalds AND NOT "Burger King"

        

5. **Attribute Specific Queries**: Specify an attribute to search in particular parts of the document.
   ```
   title:example
   text:"exact phrase"
   ```

### Useful Examples of Grouping Search Elements

(...) Use parentheses to group clauses and form sub-queries.

```
(cocacola OR pepsi) AND (finance NOT crime)
```

### Examples of Lucene Queries Most Used by Our Clients

Here are some query examples to illustrate the use of Lucene syntax in our News API:

- Proximity Searches (or near): Find words that are a certain distance apart.

   ```
   "financial crime"~5
   ```
   the match will be if both words are found and they are located within a maximum distance of 5 characters between them

- Search for articles that contain the word "technology":

  ```
  technology
  ```

- Search for articles with the exact phrase "artificial intelligence":

  ```
  "artificial intelligence"
  ```

- Search for articles with "climate" in the title and "change" in the content:

  ```
  title:climate AND content:change
  ```

- Search for articles that mention "economy" but not "recession":
  ```
  economy NOT recession
  ```

## Conclusion

Using Lucene query syntax with the TrawlingWeb News API allows you to create precise and complex searches, ensuring that you retrieve the most relevant data. For a more comprehensive understanding of Lucene query syntax, refer to the [official Lucene documentation](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

If you have any questions or need further assistance, please contact our support team.

---
**Contact Us:**
If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
- [SAT Email](mailto:support@trawlingweb.com)
- [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
- [SAC Email](mailto:gestion@trawlingweb.com)

**Sales Support (Sales):**
- [Sales Email](mailto:sales@trawlingweb.com)
