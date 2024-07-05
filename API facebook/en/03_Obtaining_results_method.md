# Facebook API - Method GET /posts

It allows to obtain the captured result of each configured Facebook Worker. You can use temporary delimiters to narrow the content returned.

# GET Parameters

Let's see the structure of the sample query:

```
https://facebook.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                   |
| :------- | :-------------------------------------------- |
| protocol | It can be **http** as **https**               |
| domain   | Address of the API facebook.trawlingweb.com   |
| method   | posts                                         |
| workerid | WORKERID access to the system of TrawlingWeb. |

## QUERY Parameters

| Parameter | Description                                                            | Default                                          | Example            |
| :-------- | :--------------------------------------------------------------------- | :----------------------------------------------- | :----------------- |
| token     | APIKEY of access of the client to the system of TrawlingWeb.           | Required value                                   | ?token={APIKEY}    |
| ts        | It is the initial temporal delimiter. Unix Time format in milliseconds | Delimit to 1 months in the past from the request | &ts=1518472804000  |
| tsi       | It is the final temporal delimiter. Unix Time format is milliseconds   | Delimit with the date of petition                | &tsi=1524818189854 |

# Output Response - RESPONSE

One time it is launched petition to API Facebook, this will return a structured response data:

## Data of publication

| Field                        | Description                                                                                   | Findable | Sortable |  Type   |           Format            |
| ---------------------------- | --------------------------------------------------------------------------------------------- | :------: | :------: | :-----: | :-------------------------: |
| id                           | Identification code assigned by Trawlingweb to each tracked publication.                      |    No    |    No    | String  |                             |
| type                         | Type of publication (posts, photos, photo, notes, permalink, videos)                          |    No    |    No    | String  |                             |
| url                          | Url of the publication                                                                        |    No    |    No    | String  |                             |
| likes_num                    | Number of likes                                                                               |    No    |    No    | Integer |                             |
| comments_num                 | Number of comments                                                                            |    No    |    No    | Integer |                             |
| shared_num                   | Number of shared                                                                              |    No    |    No    | Integer |                             |
| published                    | Post date published                                                                           |    No    |    No    |  Date   |        ISO 8601-UTC         |
| language                     | Language of the publication (Available when the language is detected with the available text) |   Yes    |    No    | String  |          ISO 639-1          |
| language_detection_precision | Precision of the detection (Available when the language is detected with the available text)  |    No    |    No    | Integer |                             |
| crawled                      | Id crawled                                                                                    |    No    |   Yes    | Integer | UNIX Timestamp milliseconds |

## User data

| Field            | Description               | Findable | Sortable |  Type  | Format |
| ---------------- | ------------------------- | :------: | :------: | :----: | :----: |
| user_name        | Username                  |    No    |    No    | String |        |
| user_screen_name | Username shown            |    No    |    No    | String |        |
| user_url         | Url User, Channel or Page |    No    |    No    | String |        |

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
        "id" : "...",
        "user_name" : "...",
        "user_screen_name" : "...",
        "user_url" : "...",
        "type" : "...",
        "url" : "...",
        "text" : "...",
        "likes_num" : "...",
        "comments_num" : "...",
        "shared_num" : "...",
        "published" : "...",
        "crawled" : "...",
        "language": "es",
        "language_detection_precision": ".."
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Facebook - Best practices

In order to use the API it is necessary to call an endpoint URL with its private access token and its Worker id.
You can generate the URL of your call in our Visual API Tester (you must access https://dashboard.trawlingweb.com/workers).

## Data Integrity

Each API request can return a maximum of 100 messages matching your query. However, there may be many more results that match your filter parameters. To consume all the data, you must continue making calls to the URL indicated in the parameter **next** of the output of each request.

## Outcome example

```
requestLeft	9999999
totalResults	295404987
next	"http://facebook.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
```

## Pagination

When making requests to the POST methods, they return a maximum of 100 results. A url of next is enabled to continue with the obtaining if they surpass this amount.
