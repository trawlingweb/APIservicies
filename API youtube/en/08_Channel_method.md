# API YOUTUBE - GET Method /channel

Allows get available comments of a concret Channel.

Content returned are stadistics of the Channel requested.

# GET Parameters

Let's see the structure of the example query:


````
https://youtube.trawlingweb.com/channel/{ID_CHANNEL}/?token={APIKEY}
````

## PATH Parameters

| Element | Description                                                 |
|:--------|:------------------------------------------------------------|
| protocol | It can be like **http** like **https** |
| domain | Direction of the API youtube.trawlingweb.com |
| method | Method used CHANNEL. Required value |
| ID_CHANNEL | ID of the channel to obtain its data. Required value |
| parameters | Query parameters |

## QUERY Parameters

| Parameter | Description  | Default | Example | 
|:----------|:-------------|:-------|:-----------|
| token | Access code of client to the system of TrawlingWeb.| Required value |  ?token={APIKEY}


# Output Response - RESPONSE

One time it is launched petition to API, this will return structured data in function of method of obtain:


## Channel data

| Field | Description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| id | ID that Youtube uses for identify this channel. | String | Alphanumeric string |

## Channel statistics

| Field | Description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| viewCount | Quantity of times that video has been reproduced. | Number | Integer |
| commentCount | Number of comments on this channel. | Number | Integer |
| hiddenSubscriberCount | Whether or not the number of subscribers is shown for this user. | Boolean | True/False |
| subscriberCount | The number of subscribers that the channel has. | Number | Integer |
| videoCount | The number of videos uploaded to the channel. | Number | Integer |

## Petition data

| Field | Description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| requestLeft | Total of pending queries of the subscription | Integer |

## Example of response in json format:

````json
"response" : {
  "data" : {
    "id" : "...",
    "statistics" : {
      "viewCount" : "...",
      "commentCount" : "...",
      "hiddenSubscriberCount" : "...",
      "subscriberCount" : "...",
      "videoCount" : "..."
    }
  },
  "requestLeft" : "..."
}
````