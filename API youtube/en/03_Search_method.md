# API YOUTUBE - GET Method /search

Allows to carry out search on Youtube to get videos using differents operators to delimit data.

Content returned of every video make reference to the descriptive data of the video and its stadistics without the comments of it.

# GET Parameters

Let's see the structure of the example query:

````
https://youtube.trawlingweb.com/search/?token={APIKEY}&q=messi&tsi=15350188800000&ts=1547510400000&size=50
````

## PATH Parameters

|      Element       | Description                                                 |
|:-------------------|:------------------------------------------------------------|
| protocol | can be like **http** like **https**                  |
| domain | Direction of the API youtube.trawlingweb.com |
| method | method used for SEARCH |
| parameters | Query parameters |

## QUERY Parameters

| Parameter | Description  |Default |Example    | 
|:----------|:-------------|:-------|:-----------|
|  token   | APIKEY of access of the client to the system of TrawlingWeb.| Required value |  ?token={APIKEY}
| q         | Expression constructed with the words or key expressions that configure filters of search| &q=messi|
| ts        | It is the initial temporal delimiter. Unix Time format in milliseconds | Delimit to 1 months in the past from the request | & ts = 1518472804000 | &ts=1518472804000|
| tsi       | It is the final temporal delimiter.Unix Time format is milliseconds | Delimit to 1 months in the past fromt the request |&tsi=1524818189854|
| size      | Number of videos that can be retrieved per page. TrawlingWeb breaks data delivery into blocks of up to 50 documents. Each block of an effective query. In this way, we can configure the size of the blocks by setting their value between 1 and 50.|50| &size=50|

# Output Response - RESPONSE

One time it is launched petition to API, this will return structured data in function of method of obtain:


## Data of search of videos

| Field | Description | Type | Format |
| ------- | ---------|:--------:|:---------:|
| id | ID that Youtube uses for identify in exclusive way a video. | String | Alphanumeric string |
| url | Url of display. | String | Alphanumeric string |
| urlShort | Url of shortened display | String | Alphanumeric string | 
| urlEmbed | Url of incrustation. | String |  Alphanumeric string |
| published | Time and Date when video was uploaded.  | Date | ISO 8601-UTC |
| channelId | ID that Youtube uses for identify of an exclusive way the channel that video was uploaded. | String | Alphanumeric string |
| channelTitle  | Title of video. | String | Alphanumeric string |
| description | Description of video.| String| Alphanumeric string |
| thumbnails | Map of images in miniature associated with the video. For every object in the map, the key is the name of the image in miniature, and the value is an object that contains another information about the bullet point. Values of valid key are:  **default:** Image in miniature predetermined. Bullet for a video, or of a resource that makes a reference to a video, like one element of one playlist or the result of a search, is 120 pixels of width and 90 pixels of height. Bullet predetermined for a channel is 88 pixels of width and 88 pixels of height.**medium:** Highest resolution image version in miniature. For a video(or one resourcce that makes reference to a video)this image is 320 pixels of width and 180 pixels of height. For a channel this image is 240 pixels of width and 240 pixels of height **high:** Highest resolution image version in miniature. For a video(or resource that makes reference to a video), this image is 480 pixels of width and 360 pixels of height. For a channel this image is 800 pixels of width and 800 pixels of height. | List | Alphanumeric string |
| tags | This field is visible for who upload video. | List | Alphanumeric string |
| categoryId | Category of video of youtube associated with video  | Number | Integer |
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
| totalResults | Total approximate of found results of the query | Entero |
| pageResults | Number of listed videos | Integer |
| next | URL to continue with pagination and like that obtain all results | String |

## Example of response in json format:

```
"json"
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
      "default":{
          "url":"...",
          "width":"...",
          "height":".."
      },
      "medium":{
          "url":"...",
          "width":"...",
          "height":".."
      },
      "high":{
          "url":"...",
          "width":"...",
          "height":".."
      },
      "standard":{
          "url":"...",
          "width":"...",
          "height":".."
      },
      "maxres":{
          "url":"...",
          "width":"...",
          "height":".."
      }
    },
    "tags" : ["...","...","..."],
    "categoryId" : "...",
    "liveBroadcastContent" : "...",
    "viewCount" : "...",
    "likeCont" : "...",
    "dislikeCount" : "...",
    "favoriteCount" : "...",
    "commentCount" : "..."
  }],
  "requestLeft" : "...",
  "totalResults" : "...",
  "restResults" : "...",
  "next" : "..."
}
````
# API YOUTUBE - Basic queries

Youtube's API allows to do the same queries as you are doing in the actual search of youtube's web. Criterion that applies when you filter videos are settled down by Youtube

## Booleans

|  Operator   | Use                                                                                                                                               |      Example       |
|:-----------:|:--------------------------------------------------------------------------------------------------------------------------------------------------|:------------------:|
| __AND__ | The operator __AND__ is an operator implied by including various terms with space. It will appear in the retrieved videos. Also can use this symbol __+__                                                                                     | "Messi" "Girona"  |
| __OR__ | The operator  __OR__ is settled down with __\|__ .Videos retrieved, it could appear as "__x__", or appear as "__y__" or can appear both mentioned.Its recommended use __()__ to avoid errors. | ("Messi"\|"Girona") |
|  __NOT__  | The operator __NOT__ is settled down by __-__ .Its not retrieved documments that include "__x__"                                                                                                |     -Messi      |


## Parenthesis

Use parenthesis to encapsulate OR declarations to the right use of search engines.

For example: *(Barcelona|Madrid|París)*


## Other filtrable terms

### Search of videos with terms "together"
	Homemade potato omelette

### Search for videos with terms in the title
	allintitle:Walt Disney

### Search for videos that contains combinatios with words
	"U2 Melbourne 2006"

### Search for videos on channel
	Elvis Presley, channel

### Search for videos on movie
	Charlie Chaplin, movie

### Search for videos on 4k
	Tokio, 4k

### Search for videos in HD
	Trailer de Star Trek, hd

### Search for videos in SD
	Moscú, sd

### Search for videos in ED
	Madagascar, 3d

### Search for videos for duration lower than 2 minutes
	Simpsons, short

### Search for videos for minimun duration than 20 minutes

	Spiderman, long

### Search for live videos
	zoo, live

### Search for videos with time
	noticias, today
	noticias, this week
	noticias, this month
	noticias, this year

### Search for videos in official channels
	The show must go on, partner

### Search for videos in playlist
	Queen, playlist

### Search for videos using boolean concept(NOT)
	android -china

### Search for videos using boolean concept(AND)
)
	Barcelona AND Paris

### Search for videos using boolean concept(OR)

	Barcelona OR Paris

### Search of combined videos the previous ones
	(Barcelona AND Paris) -messi ,4k , long

# API YOUTUBE - Best practices

With the purpose to use API its necessary call to an URL with final dot with its private access token. Can generate URL of its call in our visual Tester of the API (that should access to
https://dashboard.trawlingweb.com/playground).



## Data integrity

Every request to the API will give a maximun number of elements coincidents of the request. Even so, could have more results that coicident with your filter parameters. To consume all data should follow calls to the URL selected in the parameter **next** of the output request.



## Example of output

````
requestLeft	9999999
totalResults	295404987
next	"http://youtube.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&q=messi"
}
````



## Pagination

When you make requests to methods SEARCH it is returned maximum of 50 videos. It is enabled an url of next to continue with the obtaining videos if those overcome those quantity.