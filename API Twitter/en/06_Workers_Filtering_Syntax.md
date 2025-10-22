# Using Basic Boolean Queries in the TrawlingWeb Twitter API

TrawlingWeb APIs accept boolean queries combined with Lucene syntax expressions. Below, we show some practical examples to help you have a better experience and optimize your searches and results when using the Twitter API.

## Always within `q=`
Remember that these boolean expressions can only be used within the q= parameter in the API call and must be combined with the necessary PATH filters and parameters.


## Essential Boolean Operators AND, OR, and NOT

Boolean queries allow you to combine keywords or phrases using specific operators. Below are the available operators and some useful examples:

|  Operator   | Usage                                                                                                   |       Example        |
| :---------: | :------------------------------------------------------------------------------------------------------ | :------------------: |
| x **AND** y | "**x**" and "**y**" will appear in the retrieved documents.                                              | "Messi" AND "Girona"  |
| x **OR** y  | "**x**", "**y**", or both will appear in the retrieved documents. Parentheses are recommended.           | ("Messi" OR "Girona") |
|  **NOT** x  | Documents that include "**x**" will not be retrieved.                                                    |      NOT "Messi"      |

### Parentheses

Use parentheses to encapsulate OR statements and ensure that search engines execute the query correctly. The OR operator is interpreted as "I would like at least one of these terms."

For example: _(Barcelona OR Madrid OR Paris)_

### Quotation Marks

Quotation marks should be used to search for exact phrases consisting of more than one word. Without quotation marks, you might get documents with the words split into individual components.

For example: _White House_

Without quotation marks, the results might include pages containing _White_ and _House_, but not necessarily together. Using quotation marks, you indicate to the system that it should only return pages that include the exact phrase in that order.

For example: _"White House"_

# Using Lucene Query Syntax

TrawlingWeb APIs allow queries that can contain boolean operators combined with Lucene syntax expressions, offering a powerful tool for performing complex and precise searches. The Lucene query syntax is designed to be intuitive and expressive.

***Remember that these boolean expressions can only be used within the q= parameter in the API call and must be combined with the necessary PATH filters and parameters.***

Below, we present some key features and useful examples to optimize your user experience:

1.  **Term Query**: Searches for a specific term.

    ```
    cocacola
    ```

2.  **Phrase Query**: Searches for an exact phrase enclosed in double quotes.

    ```
    "cherry flavored coke"
    ```

3.  **Wildcard Queries**: Use `?` to replace a single character or `*` to replace zero or more characters.

    ```
    - ambigu? : (returns ambiguous or ambigua)
    
    - exam* : (returns, among others, results containing words like example, examples, exemplary, etc.)
    
    - *finances : (returns, among others, results containing words like microfinances, finances, macrofinances, etc.)
    ```

4.  **Boolean Operators**
    Use `AND`, `OR`, and `NOT` to combine multiple terms or phrases.

        Examples

        AND: This operator is used to find records that contain both terms or phrases.

        Mcdonalds AND "Burger King"
        
        OR: This operator is used to find records that contain at least one of the terms or phrases.

        Mcdonalds OR "Burger King"
        
        NOT: This operator is used to exclude records that contain the following term or phrase.

        Mcdonalds AND NOT "Burger King"

5. **Attribute-Specific Queries**: Specify an attribute to search in particular parts of the document.
    ```
    title
    text:"exact phrase"
    ```

### Useful Examples of Grouping Search Elements

(...) Use parentheses to group clauses and form subqueries.

```
(coca-cola OR pepsi) AND (finance NOT crime)
```


### Examples of Lucene Queries Most Used by Our Clients

Here are some query examples to illustrate the use of Lucene syntax in our News API:

* Search for articles containing the word "technology":

```
technology
```

* Search for articles with the exact phrase "artificial intelligence":

```
"artificial intelligence"
```

* Search for articles with "climate" in the title and "change" in the content:

```
title:change AND text:climate
```

* Search for articles that mention "economy" but not "recession":

```
economy NOT recession
```


### More Information

For more details, consult the complete Lucene syntax manual ([here](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)), which is the basis of our search engine.

## Conclusion and More Information

Using the Lucene query syntax with the TrawlingWeb News API allows you to create precise and complex searches, ensuring you retrieve the most relevant data. For a more comprehensive understanding of the Lucene query syntax, consult the [official Lucene documentation](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

If you have any questions or need further assistance, please contact our support team.

---

# Contact

If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
* [Email SAT](mailto:support@trawlingweb.com)
* [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
* [Email SAC](mailto:gestion@trawlingweb.com)

**Sales Support:**
* [Email Sales](mailto:sales@trawlingweb.com)
