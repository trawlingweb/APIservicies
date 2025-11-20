
# API Twitter - POST Method /create

Allows creating new Workers with their words.

# What is a Worker?

A Worker in TrawlingWeb is an entity configured by the user to perform specific searches on social networks using Keywords. These Keywords are search terms configured within the Worker and are based on the credits purchased (1 credit = 1 Keyword).

## Creating and Configuring Workers

The user can create and define search terms for each Worker directly in the dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) or using the method provided by the API. Once a Worker is created, it begins its deployment to start its configuration process, which can take up to an hour.

## Functionality of Workers

* **Keywords**: Workers function as a list of keywords. They use the configured Keywords to perform searches on social networks.
* **Search Process**: Workers deliver the Keywords to TrawlingWeb's spiders to execute their searches on the social network.
* **Delivery Process**: Each time the client calls the Worker, it uses the list of Keywords to launch the search against the database of results obtained by TrawlingWeb and retrieve only those results that are related to the list of Keywords.

Implementing and managing Workers efficiently allows users to maximize the relevance and accuracy of the data captured, adapting to the specific needs of their social media analysis and monitoring.


# POST Parameters

Let's see the structure of the example query:

```
https://twitter.trawlingweb.com/create/?token={APIKEY}
```

## PATH Parameters:

| Element  | Description                                 |
| :-------- | :------------------------------------------ |
| protocol | Can be either **http** or **https**     |
| domain   | API address twitter.trawlingweb.com |
| method    | create                                      |

## QUERY Parameters:

| Parameter | Description                                              | Default           | Example         |
| :-------- | :------------------------------------------------------- | :---------------- | :-------------- |
| token     | Client's access APIKEY to the TrawlingWeb system. | Mandatory value | ?token={APIKEY} |

## BODY Parameters:

| Parameter   | Description                            | Default           | Limits                                                   |
| :---------- | :------------------------------------- | :---------------- | :-------------------------------------------------------- |
| description | Description that the Worker must have. | Mandatory value | String not exceeding 200 characters                       |
| words       | Search words.                  | Mandatory value | The number of words must not exceed the agreed limit |

### Structure of the words parameter

The `words` parameter must be sent as a **JSON array** of text strings, where each array element represents a Keyword. Each Keyword can contain advanced Twitter syntax (hashtags, mentions, boolean operators, filters, etc.).

**Important recommendation for searches with `from:`**: When you need to search for tweets from multiple accounts, you can chain up to a maximum of 10 accounts using the OR operator within a single expression. This allows you to optimize credit usage by grouping multiple accounts into a single Keyword.

### Example body in JSON format:

```json
{
    "description": "Example Worker for brand monitoring",
    "words": [
        "from:cocacola OR from:pepsi OR from:trawlingweb",
        "cocacola",
        "#pepsi",
        "cocacola lang:fr"
    ]
}
```

In this example, the Worker is created with 4 Keywords:
1. A complex search with multiple accounts using the OR operator (maximum 10 accounts per expression)
2. A simple word: "cocacola"
3. A hashtag: "#pepsi"
4. A word with language filter: "cocacola lang:fr"

Each element in the `words` array consumes 1 credit (1 credit = 1 Keyword).

# Output Response - RESPONSE

Once a request is sent to the Twitter API, it will return a response structured as follows:

## Status 200 - Return Data

| Field  | Description                          |  Type  |
| ------ | ------------------------------------ | :----: |
| worker | Identifier of the created Worker.     | String |
| msg    | Description indicating successful action | String |

## Example response in json format:

```json
"response" : {
    "worker" : "...",
    "msg" : "..."
}
```

## Status 400 - Return Data

| Field | Description           |  Type  |
| ----- | --------------------- | :----: |
| error | Description of the error | String |

## Example response in json format:

```json
"response" : {
    "error" : "..."
}
```

## Better searches with Twitter syntax

Twitter uses its own advanced syntax to perform specific and detailed searches within its platform. This syntax allows filtering results by keywords, hashtags, mentions, locations, and dates, among other parameters. Additionally, when defining keywords for a Worker, this same syntax can be used to launch precise queries against Twitter's search engine. This maximizes the efficiency and relevance of the data captured by each Worker, facilitating more effective monitoring and analysis of Twitter conversations.

Here is a list of elements you can combine with your keywords when creating them within a worker:

| Type              | Description                                                                          | Example keyword                | Result                                                                           |
| ----------------- | :----------------------------------------------------------------------------------- | :----------------------------- | ----------------------------------------------------------------------------------- |
| Hashtag           | Terms referenced with the hashtag #                                          | #pepsi                         | returns posts that contain hashtag (#) pepsi                                     |
| At                | Users referenced with the at @                                               | @cocacola                      | returns posts in which @cocacola has been tagged/mentioned                   |
| Simple String     | Word with alphanumeric terms without special characters                         | Studio54                       | returns posts that contain the word "Studio54"                                  |
| Complex String    | Words with alphanumeric terms without special characters separated by spaces | Cocoa Cola 2019                | returns any post that contains some or all of these words from the example |
| Exact Search      | Specific words or phrases in quotes                                         | "cocacola with ice"           | returns posts that contain exactly the phrase "cocacola with ice"             |
| OR Search         | Multiple words separated by OR to broaden results                          | Cocacola OR Pepsi              | returns posts that contain "Cocacola" or "Pepsi" (or both)                       |
| Without words (NOT)  | Exclude specific words from the search                                          | Cocacola -pepsi                | returns posts that contain "Cocacola" but excludes those that contain "pepsi" |
| Specific Hashtag  | Search for specific hashtags                                                     | #openai                        | returns posts that contain the hashtag (#) openai                                 |
| From an account   | Search for tweets sent by a specific account. Up to 10 accounts can be chained with OR within a single expression | from:cocacola                  | returns posts published by the @cocacola account. Example with multiple: `from:account1 OR from:account2 OR ... OR from:account10` |
| To an account     | Search for tweets sent to a specific account                                  | to:pepsi                       | returns posts directed to the @pepsi account                                        |
| Mention of account| Search for tweets that mention a specific account                               | @cocacola                      | returns posts in which @cocacola has been tagged/mentioned                |
| Near location     | Search for tweets sent near a specific location                        | "buy cocacola" near:Quito  | returns posts that contain "buy cocacola" sent near Quito            |
| Within radius     | Search for tweets sent within a specific radius                            | cocacola near:lima within:15km | returns posts that contain "cocacola" sent within 15km of Lima           |
| Since date        | Search for tweets sent since a specific date                               | cocacola since:2022-02-17      | returns posts that contain "cocacola" published since February 17, 2022  |
| Until date        | Search for tweets sent until a specific date                               | pepsi until:2022-02-17         | returns posts that contain "pepsi" published until February 17, 2022    |
| Question          | Search for tweets that contain questions                                           | pepsi ?                        | returns posts that contain "pepsi" and that are questions                          |
| With links        | Search for tweets that contain links                                             | cocacola filter:links          | returns posts that contain "cocacola" and that include links                    |
| Specific source   | Search for tweets published from a specific source                            | pepsi source:twitterfeed       | returns posts that contain "pepsi" published from the twitterfeed source        |
| Word with specific language | Search for tweets published in a specific language. Must be in ISO Alpha II     | pepsi lang:fr                  | returns posts that contain "pepsi" published in French (ISO Alpha II: fr)      |

## Reserved characters in search words

> Reserved characters are: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

# Contact

If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
* [Email SAT](mailto:support@trawlingweb.com)
* [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
* [Email SAC](mailto:gestion@trawlingweb.com)

**Sales Support:**
* [Email Sales](mailto:sales@trawlingweb.com)
