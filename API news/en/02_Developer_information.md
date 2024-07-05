# API NEWS & BLOGS - Things that every developer should know

## API

Trawlingweb.com API NEWS & BLOGS is an API REST, so although the data is intended to be consumed as a data stream, it is necessary to call the API continuously in order to receive the data batches.

## URL Structure

### The URL query call has three parts:

- Authentication
- The HTTP GET parameters string to set the timestamp, size of page and reception format file.
- The query string to set up the pairs **filters:value** that specifies the wanted data.

## Authentication

Authentication is effective with an unique valid access token included in the URL API call. Client can find his access token in his client control pannel.

## Rate limit

All API plans include a single unique access token, with a built-in querying limitation of one request per second. To overcome this limit, a second plan must be added.

## Output formats

Two file formats are avaiable in order to receive the response to the query:

| Format | Description                |
| ------ | :------------------------- |
| JSON   | JavaScript Object Notation |
| XML    | eXtensible Markup Language |

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
