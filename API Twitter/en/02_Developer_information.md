# API Twitter - Things that every developer should know

## API

Trawlingweb.com API NEWS & BLOGS is an API REST, so although the data is intended to be consumed as a data stream, it is necessary to call the API continuously in order to receive the data batches.

## Authentication

Authentication is effective with an unique valid access token included in the URL called the API next to the worker's id to ingest.
You can find your access token and your Worker ids in the control panel.
(https://dashboard.trawlingweb.com/workers)

## Rate limit

All Twitter API plans include a single unique access token along with the specific identifier of each Worker.
A request speed limitation of one is established every 5 seconds.
To overcome this limit, it will have to be solved specifically.

## Output formats

Two file formats are avaiable in order to receive the response to the query:

| Format | Description                |
| ------ | :------------------------- |
| JSON   | JavaScript Object Notation |

## HTTP / HTTPS security support API

Twalingwerb.com supports both HTTP and HTTPS (SSL) endpoint calls.

## GET requests

API is called with GET requests. In order to optimeze the requests, it's better to make several short queries than a very long single query.

## HTTP status codes

| Code | Description                                     |
| ---- | :---------------------------------------------- |
| 200  | Success!                                        |
| 401  | Unauthorized user or without available tokens   |
| 404  | Syntax error                                    |
| 500  | The query could not be executed: internal error |
| 503  | Service temporarily unavailable                 |
| 429  | Exceeds rate limit                              |

NOTE: Detail of the error explained in the return of the request.
