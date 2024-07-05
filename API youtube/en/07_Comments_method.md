# API YOUTUBE - GET Method /comments

Allows get available comments of a concret video.

Content returned are the comments of the requested video without stadistic and descriptive data of it.

# GET Parameters

Let's see the structure of the example query:


````
https://youtube.trawlingweb.com/comments/{ID_VIDEO}/?token={APIKEY}
````

## PATH Parameters

| Element | Description |
|:--------|:------------|
| protocol | It can be like **http** like **https** |
| domain | Direction of the API youtube.trawlingweb.com |
| method | Method used COMMENTS. Required value |
| ID_VIDEO | ID of video to get data from method. Required value |
| parameters | Query parameters |

## QUERY Parameters

| Parameter | Description  | Default | Example | 
|:----------|:-------------|:-------|:-----------|
| token | Access code of client to the system of TrawlingWeb.| Required value | ?token={APIKEY} |

# Output Response - RESPONSE

One time it is launched petition to API, this will return structured data in function of method of obtain:


## Video comment data

| Field | Description | Type | Format |
|:-------|---------|:--------:|:---------:|
| id | ID of comment of video. | String | Alphanumeric string |
| totalReplyCount | Number of comments of video. | String | Alphanumeric string |
| isPublic | This setting indicates whether the thread, including all comments and comment responses, is visible to all YouTube users. Valid values ​​for this property are: **true** o **false** | String | Alphanumeric string | 
| authorDisplayName | Name to show of user that published the comment | String | Alphanumeric String |
| authorProfileImageUrl | URL of user's avatar that published the comment  | String | Alphanumeric string |
| authorChannelUrl | The URL of the YouTube channel of the author of the comment, if available | String | Alphanumeric string |
| authorChannelId | The YouTube channel ID of the author of the comment, if available. | String | Alphanumeric string |
| textDisplay | Comments text. Keep in mind that even plain text may differ from the original text. For example, you can replace the links in the titles of the articles.| String | Alphanumeric string |
| textOriginal | The original unprocessed text of the comment as it was originally published or was last updated. The original text is only returned if it is accessible to the authenticated user, which is only guaranteed if the user is the author of the comment. | String | Alphanumeric string |
| viewerRating | The rating that the viewer has given to this comment. Note that this property does not currently identify the ratings of dislike, although this behavior is subject to change. Meanwhile, the value of the property is similar if the viewer has rated the comment positively. The value is none in all other cases, including that the user has given a negative rating to the comment or has not rated the comment. Valid values ​​for this property are: **like** o **none** | String | Alphanumeric string |
| likeCount | Number of users that indicate that they liked the comment, giving it a positive rating. | Number | Whole |
| published | Date and time the comment was uploaded. | Date | ISO 8601-UTC |
| updated | Date and time the comment was updated. | Date | ISO 8601-UTC |
| canRate | This setting indicates whether the current viewer can rate the comment. Valid values ​​for this property are: ** true ** or ** false ** | String | Alphanumeric String |
| replies | List of comments if they exist | Number | Whole |
| replies.id | ID of the video comment replica. | String | Alphanumeric String |
| replies.totalReplyCount | Number of comments comments on the video. | String | Alphanumeric String |
| replies.isPublic | This is an indication for all YouTube users. Valid values ​​for this property are: **true** or **false** | String | Alphanumeric String |
| replies.authorDisplayName | The name to show the user who publishes the comment replica. | String | Alphanumeric String |
| replies.authorProfileImageUrl | The avatar URL of the user who posted the comment replica. | String | Alphanumeric String |
| replies.authorChannelUrl | The URL of the YouTube channel of the author of the comment reply, if available. | String | Alphanumeric String |
| replies.authorChannelId | The ID of the author's YouTube channel the reply of the comment, if available. | String | Alphanumeric String |
| replies.textDisplay | The text of the reply of the comment. Keep in mind that even plain text may differ from the original text. For example, you can replace video links with video titles. String | Alphanumeric String |
| replies.textOriginal | The original text without processing the reply of the comment as it was initially published or was last updated. The original text is only returned if it is accessible to the authenticated user, which is only guaranteed if the user is the author of the comment. | String | Alphanumeric String |
| replies.viewerRating | The rating that the viewer has given to this reply of the comment. Note that this property does not currently identify the ratings of dislike, although this behavior is subject to change. Meanwhile, the value of the property is similar if the viewer has rated the comment positively. The value is none in all other cases, including that the user has given a negative rating to the comment or has not rated the comment. Valid values ​​for this property are: **like** or **none** | String | Alphanumeric String |
| replies.likeCount | Number of users who indicated that they liked the reply of the comment, giving it a positive rating. | Number | Whole |
| replies.published | Date and time the comment was uploaded. | Date | ISO 8601-UTC |
| replies.updated | Date and time when the reply of the comment was updated. | Date | ISO 8601-UTC |
| replies.canRate | This setting indicates whether the current viewer can rate the comment replica. Valid values ​​for this property are: **true** or **false** | String | Alphanumeric String |
| replies.parentId | The unique ID of the parent comment. This property is only set if the comment was sent as a reply to another comment. | Boolean | 0 or 1 |

## Petition data

| Field | Description | Type |
|:-----|:------------|:-------:|
| requestLeft | Total of pending queries of the subscription | Integer |
| totalResults | Total approximate of found results of the query | Integer |
| pageResults | Number of listed videos | Integer |
| next | URL to continue with pagination and like that obtain all results | String |

## Example of response in json format:

````json
"response" : {
  "data" : {
    "id" : "...",
    "totalReplyCount" : "...",
    "isPublic" : "...",
    "authorDisplayName" : "...",
    "authorProfileImageUrl" : "...",
    "authorChannelUrl" : "...",
    "authorChannelId" : "...",
    "textDisplay" : "...",
    "textOriginal" : "...",
    "viewerRating" : "...",
    "likeCount" : ["...","...","..."],
    "published" : "...",
    "updated" : "...",
    "canRate" : "...",
    "replies" : [{
      "replies.id" : "...",
      "replies.totalReplyCount" : "...",
      "replies.isPublic " : "...",
      "replies.authorDisplayName" : "...",
      "replies.authorProfileImageUrl" : "...",
      "replies.authorChannelUrl" : "...",
      "replies.authorChannelId" : "...",
      "replies.textDisplay" : "...",
      "replies.textOriginal" : "...",
      "replies.viewerRating" : "...",
      "replies.published" : "...",
      "replies.updated" : "...",
      "replies.canRate" : "...",
      "replies.parentId" : "..."
    }]
  },
  "requestLeft" : "...",
  "totalResults" : "...",
  "restResults" : "...",
  "next" : "..."
}
````