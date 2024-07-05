# API YOUTUBE - things every developer should know

## API REST

Trawlingweb.com is an API REST, so even though data is destinated to be consumed as data stream, its necessary to call the API continuosly in order to receive data batches.


## URL Structure


### Url query has three parts:

- Authentication
- HTTP GET parameter string for the authentication, temporal period.
- String request filter and__filters:value__ that specifies the needed data.)



## Authetication

Authentication is confirmed by an unique access token aproved in the URL call API. Client can find his unique access token via control panel.



## Rate limits

All API YOUTUBE plans include a single unique  access token, with a limitation of velocity of 1 request every 5 seconds. To overcome this limit you need to request it.



## Output formats

We offer data in the following output format:

| Format | Description |
|-----------------|:---------------------------------------------|
| JSON  |  JavaScript Object Notation |
|  XML   | eXtensible Markup Language |



## HTTP / HTTPS security support API

Twalingweb.com supports both HTTP and HTTPS (SSL) endpoint calls.



## Petitions GET

You can call API with GET petitions. If you do large calls to the API, we recommend to use short calls to optimize it.



## HTTP codes states
| Code         | Description   |
| ------------- |:---------------|
| 200 | Success!|
| 401 | Unauthorized user or without available tokens|
| 404 | Syntax error |
| 500 | The query could not be executed: internal error |
| 503 | Service temporarily unavailable |
| 429 | Exceeds rate limit |

NOTE: Detail of the error explained in the return of the request.


