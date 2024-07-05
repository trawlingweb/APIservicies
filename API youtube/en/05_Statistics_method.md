# API YOUTUBE - GET Method /statistics

Allows get latest available stadistics of a concret video.

Content returned are stadistics of the video requested.

# GET Parameters

Let's see the structure of the example query:

````
https://youtube.trawlingweb.com/statistics/{ID_VIDEO}/?token={APIKEY}
````

## PATH Parameters

|      Element       | Description                                                 |
|:-------------------|:------------------------------------------------------------|
| protocol | It can be like **http** like **https** |
| domain | Direction of the API youtube.trawlingweb.com |
| method | Method used STATISTICS. Required value |
| ID | ID of video to get data from method. Required value |
| parameters | Query parameters |

## QUERY Parameters

| Parameter | Description  | Default | Example    | 
|:----------|:-------------|:-------|:-----------|
| token     |Access code of client to the system of TrawlingWeb.| Required value |  ?token={APIKEY}

# Output Response - RESPONSE

One time it is launched petition to API, this will return structured data in function of method of obtain:


## News stadistics

| Field | Description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| id |  ID that Youtube uses for identify in exclusive way a video. | String | Alphanumeric string |
| viewCount | Quantity of times that video has been reproduced | Number | Integer |
| likeCont | Number of users who indicated that they liked the video, gave a positive rating | Number | Integer |
| dislikeCount  |Number of users who indicated that they did not like the video, giving it a negative rating. | Number | Integer |
| favoriteCount | Number of users who currently have video marked as favorite video. | Number | Integer |
| commentCount  | Number of comments on a video. | Number | Integer |

## Petition data

| Field | Description | Type |
|:-----|:------------|:-------:|
| requestLeft | Total of pending queries of the subscription | Integer |

## Example of response in json format:

````json
"response" : {
  "data" : [{
    "id" : "...",
    "viewCount" : "...",
    "likeCont" : "...",
    "dislikeCount" : "...",
    "favoriteCount" : "...",
    "commentCount" : "..."
  }],
  "requestLeft" : "...",
}
````