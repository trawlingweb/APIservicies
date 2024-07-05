# API YOUTUBE - GET Method /video

Allows get latest descriptive data of a concret video.

Content returned are descritive data requested without any stadistic and comments of it.

# GET Parameters

Let's see the structure of the example query:

````
https://youtube.trawlingweb.com/video/{ID_VIDEO}/?token={APIKEY}
````

## PATH Parameters

| Element | Description                                                 |
|:--------|:------------------------------------------------------------|
| protocol | It can be like **http** like **https** |
| domain | Direction of the API youtube.trawlingweb.com |
| method | Method used VIDEO. Required value |
| ID | ID of video to get data from method. Required value |
| parameters | Query parameters |

## QUERY Parameters

| Parameter | Description  | Default | Example | 
|:----------|:-------------|:-------|:-----------|
| token     | Access code of client to the system of TrawlingWeb.| Required value |  ?token={APIKEY}

# Output Response - RESPONSE

One time it is launched petition to API, this will return structured data in function of method of obtain:


## Video data

| Field | description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| id | ID that Youtube uses for identify in exclusive way a video. | String | Alphanumeric string |
| url | Url of display. | String | Alphanumeric string |
| urlShort | Url of shortened display | String | Alphanumeric string | 
| urlEmbed | Url of incrustation | String |  Alphanumeric string |
| published | Time and Date when video was uploaded.  | Date | ISO 8601-UTC |
| channelId | ID that Youtube uses for identify of an exclusive way the channel that video was uploaded. | String | Alphanumeric string |
| channelTitle  | Title of video | String | Alphanumeric string |
| description | Description of video | String| Alphanumeric string |
| thumbnails | Map of images in miniature associated with the video. For every object in the map, the key is the name of the image in miniature, and the value is an object that contains another information about the bullet point. Values of valid key are:  **default:** Image in miniature predetermined. Bullet for a video, or of a resource that makes a reference to a video, like one element of one playlist or the result of a search, is 120 pixels of width and 90 pixels of height. Bullet predetermined for a channel is 88 pixels of width and 88 pixels of height.**medium:** Highest resolution image version in miniature. For a video(or one resourcce that makes reference to a video)this image is 320 pixels of width and 180 pixels of height. For a channel this image is 240 pixels of width and 240 pixels of height **high:** Highest resolution image version in miniature. For a video(or resource that makes reference to a video), this image is 480 pixels of width and 360 pixels of height. For a channel this image is 800 pixels of width and 800 pixels of height. | List | Alphanumeric string |
| tags | This field is visible for who upload video. | List | Alphanumeric string |
| categoryId | Category of video of youtube associated with video | Number | Integer |
| liveBroadcastContent | Indicate if content is live. Values can be   **live** o **none** | String | Alphanumeric string | 
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
    "url" : "...",
    "urlShort" : "...",
    "urlEmbed" : "...",
    "published" : "...",
    "channelId" : "...",
    "channelTitle" : "...",
    "description" : "...",
    "thumbnails" : {
      "defaul":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "medium":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "high":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "standard":{
          "url":"...",
          "width":"...",
          "height":"..."
      },
      "maxres":{
          "url":"...",
          "width":"...",
          "height":"..."
      }
    },
    "tags" : ["...","...","..."],
    "categoryId" : "...",
    "liveBroadcastContent" : "...",
    "viewCount" : "...",
    "likeCount" : "...",
    "dislikeCount" : "...",
    "favoriteCount" : "...",
    "commentCount" : "..."
  }],
  "requestLeft" : "...",
}
````