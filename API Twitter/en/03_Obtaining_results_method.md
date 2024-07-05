# Twitter API - Method GET /posts

It allows to obtain the captured result of each configured Twitter Worker. You can use temporary delimiters to narrow the content returned.

# GET Parameters

Let's see the structure of the sample query:

```
https://twitter.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                   |
| :------- | :-------------------------------------------- |
| protocol | It can be **http** as **https**               |
| domain   | Address of the API twitter.trawlingweb.com    |
| method   | posts                                         |
| workerid | WORKERID access to the system of TrawlingWeb. |

## QUERY Parameters

| Parameter | Description                                                            | Default                                          | Example            |
| :-------- | :--------------------------------------------------------------------- | :----------------------------------------------- | :----------------- | ----------------- |
| token     | APIKEY of access of the client to the system of TrawlingWeb.           | Required value                                   | ?token={APIKEY}    |                   |
| ts        | It is the initial temporal delimiter. Unix Time format in milliseconds | Delimit to 1 months in the past from the request | &ts=1518472804000  | &ts=1518472804000 |
| tsi       | It is the final temporal delimiter. Unix Time format is milliseconds   | Delimit with the date of petition                | &tsi=1524818189854 |                   |

# Output Response - RESPONSE

One time it is launched petition to API Twitter, this will return a structured response data:

## Data of publication

| Field                  | Description                                                                                                                                                | Findable | Sortable |  Type   | Format                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :------: | :------: | :-----: | ----------------------------- |
| id                     | Identification code assigned by Trawlingweb to each crawled post                                                                                           |    No    |    No    | String  |                               |
| hash                   | Identification code based on the text                                                                                                                      |    No    |    No    | String  |                               |
| published              | Date the post was published                                                                                                                                |    No    |    No    |  Date   | ISO 8601-UTC                  |
| crawled                | Date of capture                                                                                                                                            |    No    |   Yes    | Integer | UNIX Timestamp (milliseconds) |
| updated                | Date of update                                                                                                                                             |    No    |   Yes    | Integer | UNIX Timestamp (milliseconds) |
| post_id                | Post ID                                                                                                                                                    |    No    |    No    | String  |                               |
| url                    | Publication URL                                                                                                                                            |    No    |    No    | String  |                               |
| text                   | Descriptive text of the publication                                                                                                                        |    No    |    No    | String  |                               |
| lang                   | When present, indicates a BCP 47 language identifier corresponding to the language detected by the text machine, or "und" if no language could be detected |    No    |    No    | String  |                               |
| retweet_count          | Number of times this Tweet has been retweeted                                                                                                              |    No    |    No    | Integer |                               |
| reply_count            | Number of times this Tweet has been replied                                                                                                                |    No    |    No    | Integer |                               |
| favorite_count         | Indicates approximately how many times users on Twitter have liked this Tweet                                                                              |    No    |    No    | Integer |                               |
| reproductions_count    | Number of times this Tweet has been reproduced                                                                                                             |    No    |    No    | Integer |                               |
| user_name              | User name                                                                                                                                                  |    No    |    No    | String  |                               |
| user_screen_name       | Displayed user name                                                                                                                                        |    No    |    No    | String  |                               |
| user_url               | User URL                                                                                                                                                   |    No    |    No    | String  |                               |
| user_profile_image_url | An HTTP-based URL pointing to the user's profile image                                                                                                     |    No    |    No    | String  |                               |
| entities_url           | Mentioned links                                                                                                                                            |    no    |    no    | String  |                               |
| hashtags               | Hashtags referenced in the text                                                                                                                            |    No    |    No    | String  |                               |
| user_mentions          | Users referenced in the text                                                                                                                               |    No    |    No    | String  |                               |
| time_distance          | Hours elapsed between the publication date and the capture date                                                                                            |    No    |    No    |  Fload  |                               |
| reply                  | Indicates if it is a reply to a Tweet                                                                                                                      |    No    |    No    | Boolean |                               |

## Petition data

| Field        | Description                                                      |  Type   |
| :----------- | :--------------------------------------------------------------- | :-----: |
| requestLeft  | Total of pending queries of the subscription                     | Integer |
| totalResults | Total approximate of found results of the query                  | Integer |
| next         | URL to continue with pagination and like that obtain all results | String  |

## Example of response in json format:

```json
"response" : {
    "data" : [{
        "id": "...",
        "hash": "...",
        "published" : "...",
        "crawled" : "...",
        "updated" : "...",
        "post_id" : "...",
        "url" : "...",
        "text" : "...",
        "lang" : "...",
        "retweet_count" : "...",
        "reply_count" : "...",
        "favorite_count" : "...",
        "reproductions_count" : "...",
        "created_at" : "...",
        "user_name" : "...",
        "user_screen_name" : "...",
        "user_url" : "...",
        "user_profile_image_url" : "...",
        "entities_url" : "...",
        "hashtags" : "...",
        "user_mentions" : "...",
        "time_distance" : "...",
        "reply" : "...",
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Twitter - Best practices

In order to use the API it is necessary to call an endpoint URL with its private access token and its Worker id.
You can generate the URL of your call in our Visual API Tester (you must access https://dashboard.trawlingweb.com/workers).

## Data Integrity

Each API request can return a maximum of 500 messages matching your query. However, there may be many more results that match your filter parameters. To consume all the data, you must continue making calls to the URL indicated in the parameter **next** of the output of each request.

## Outcome example

```
requestLeft	9999999
totalResults	295404987
next	"http://twitter.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
```

## Pagination

When making requests to the POST methods, they return a maximum of 100 results. A url of next is enabled to continue with the obtaining if they surpass this amount.
