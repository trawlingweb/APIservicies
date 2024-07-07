
# API Twitter - POST Method /create

Allows creating new Workers with their words.

# What is a Worker?

A Worker in TrawlingWeb is an entity configured by the user to perform specific searches on social networks using Keywords. These Keywords are search terms configured within the Worker and are based on the credits purchased (1 credit = 1 Keyword).

## Creating and Configuring Workers

The user can create and define search terms for each Worker directly in the dashboard ([https://dashboard.trawlingweb.com/workers](https://dashboard.trawlingweb.com/workers)) or using the method provided by the API. Once a Worker is created, it begins its deployment to start its configuration process, which can take up to an hour.

## Functionality of Workers

- **Keywords**: Workers function as a list of keywords. They use the configured Keywords to perform searches on social networks.
- **Search Process**: Workers deliver the Keywords to TrawlingWeb's spiders to execute their searches on the social network.
- **Delivery Process**: Each time the client calls the Worker, it uses the list of Keywords to launch the search against the database of results obtained by TrawlingWeb and retrieve only those results that are related to the list of Keywords.

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

| Type              | Description                                                                          | Example                   |
| ----------------- | :----------------------------------------------------------------------------------- | :------------------------ |
| Hashtag           | Terms referenced with the hashtag #                                          | #pepsi                     |
| At                | Users referenced with the at @                                               | @cocacola                     |
| Simple String     | Word with alphanumeric terms without special characters                         | Studio54                  |
| Complex String    | Words with alphanumeric terms without special characters separated by spaces | Cocoa Cola 2019          |
| Exact Search      | Specific words or phrases in quotes                                         | "cocacola with ice"      |
| OR Search         | Multiple words separated by OR to broaden results                          | Cocacola OR Pepsi   |
| Without words (NOT)  | Exclude specific words from the search                                          | Cocacola -pepsi               |
| Specific Hashtag  | Search for specific hashtags                                                     | #openai                    |
| From an account   | Search for tweets sent by a specific account                                | from:cocacola         |
| To an account     | Search for tweets sent to a specific account                                  | to:pepsi           |
| Mention of account| Search for tweets that mention a specific account                               | @cocacola             |
| Near location     | Search for tweets sent near a specific location                        | "buy cocacola" near:"Argentina" |
| Within radius     | Search for tweets sent within a specific radius                            | cocacola near:lima within:15km |
| Since date        | Search for tweets sent since a specific date                               | cocacola since:2022-02-17  |
| Until date        | Search for tweets sent until a specific date                               | pepsi until:2022-02-17 |
| Question          | Search for tweets that contain questions                                           | pepsi ?                |
| With links        | Search for tweets that contain links                                             | cocacola filter:links    |
| Specific source   | Search for tweets published from a specific source                            | pepsi source:twitterfeed |

## Reserved characters in search words

> Reserved characters are: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -

# Contact

If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
- [Email SAT](mailto:support@trawlingweb.com)
- [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
- [Email SAC](mailto:gestion@trawlingweb.com)

**Sales Support:**
- [Email Sales](mailto:sales@trawlingweb.com)
