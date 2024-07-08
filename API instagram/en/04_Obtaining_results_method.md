# API Instagram - GET Method /posts

It allows to obtain the captured result of each configured Instagram Worker.
You can use temporary delimiters to narrow the content returned.

# GET Parameters

Let's see the structure of the sample query:

```
https://instagram.trawlingweb.com/posts/{WORKERID}?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                         |
| :------- | :-------------------------------------------------- |
| protocol | It can be **http** as **https**                     |
| domain   | Address of the API instagram.trawlingweb.com        |
| method   | Posts                                               |
| workerid | WORKERID of access to to the system of TrawlingWeb. |

## Query Parameters

| Parameter | Description                                                            | Default                                          | Example            |
| :-------- | :--------------------------------------------------------------------- | :----------------------------------------------- | :----------------- |
| token     | APIKEY of access of the client to the system of TrawlingWeb.           | Required value                                   | ?token={APIKEY}    |
| ts        | It is the initial temporal delimiter. Unix Time format in milliseconds | Delimit to 1 months in the past from the request | &ts=1518472804000  |
| tsi       | It is the final temporal delimiter. Unix Time format is milliseconds   | Delimit with the date of petition                | &tsi=1524818189854 |

# Output Response - RESPONSE

One time it is launched petition to API Instagram, this will return a structured response data:

## Data of the publication

| Field     | Description                                                              | Findable | Sortable |  Type   |           Format            |
| --------- | ------------------------------------------------------------------------ | :------: | :------: | :-----: | :-------------------------: |
| id        | Identification code assigned by Trawlingweb to each tracked publication. |    No    |    No    | String  |                             |
| post_id   | Id of post                                                               |    No    |    No    | String  |                             |
| type      | Type of publication(photo or video)                                      |    No    |    No    | String  |                             |
| url       | Url of the publication                                                   |    No    |    No    | String  |                             |
| media_url | Web address of multimedia contents.                                      |    No    |    No    | String  |                             |
| likes     | Number of likes                                                          |    No    |    No    | Integer |                             |
| text      | Written text of the publication                                          |    No    |    No    | String  |                             |
| published | Post date published                                                      |    No    |    No    |  Date   |        ISO 8601-UTC         |
| crawled   | Id crawled                                                               |    No    |   Yes    | Integer | UNIX Timestamp milisegundos |

## User data

| Field             | Description              | Findable | Sortable |  Type   | Format |
| ----------------- | ------------------------ | :------: | :------: | :-----: | :----: |
| user_name         | Username                 |    No    |    No    | String  |        |
| user_screen_name  | Username shown           |    No    |    No    | String  |        |
| user_publications | Number of publications   |    No    |    No    | Integer |        |
| user_followers    | Number of followers      |    No    |    No    | Integer |        |
| user_followed     | Number of followed users |    No    |    No    | Integer |        |

## Data of comments

| Field    | Description | Findable | Sortable |  Type  | Format |
| -------- | ----------- | :------: | :------: | :----: | :----: |
| comments | comments    |    No    |    No    | String |        |

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
        "post_id": "...",
        "type": "...",
        "url": "...",
        "media_url": "...",
        "user_name": "...",
        "likes": "...",
        "text": "...",
        "comments": "...",
        "published": "...",
        "crawled": "...",
        "user_screen_name": "...",
        "user_publications": "...",
        "user_followers": "...",
        "user_followed": "..."
    }],
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```

# API Instagram - Best practices

In order to use the API it is necessary to call an endpoint URL with its private access token and its Worker id.
You can generate the URL of your call in our Visual API Tester (you must access https://dashboard.trawlingweb.com/workers).

## Data Integrity

Each API request can return a maximum of 100 messages matching your query. However, there may be many more results that match your filter parameters. To consume all the data, you must continue making calls to the URL indicated in the parameter **next** of the output of each request.

## Outcome example

```
requestLeft	9999999
totalResults	295404987
next	"http://instagram.trawlingweb.com/posts/1234567891234567891234567891234567.123456789?token=1234567891234567891234567891234567891234&ts=1555327617000&tsi=1554076800000"
}
```

## Pagination

When making requests to the POST methods, they return a maximum of 100 results. A url of next is enabled to continue with the obtaining if they surpass this amount.

# Contact

If you have any questions, need assistance, or want to contract or expand your services, please contact us.

**SAT (Technical Support):**
- [SAT Email](mailto:support@trawlingweb.com)
- [Official Documentation](https://docs.trawlingweb.com)

**SAC (Administrative Support):**
- [SAC Email](mailto:gestion@trawlingweb.com)

**Sales (Sales Support):**
- [Sales Email](mailto:sales@trawlingweb.com)

