#Legal API - Things Every Developer Should Know

## REST API

Trawlingweb.com Legal API is a REST API, so even though the data is intended to be consumed as a data stream, you need to call the API continuously to receive batches of data.

## URL Structure

### The URL query call consists of three parts:

- Authentication.
- The HTTP GET parameter string for authentication, time period, pagination, and format.
- The query string that passes filter keys and respective value matches for the API to retrieve only the required data.

## Authentication

Authentication is confirmed through a unique access token provided in the API call URL. You can find your access token in the control panel.

## Output Formats

We provide data in structured format:

| Format | Description                |
| ------ | :------------------------- |
| JSON   | JavaScript Object Notation |

## HTTP/HTTPS Security Support

Trawlingweb.com supports both HTTP and HTTPS (SSL) endpoint calls.

## GET Requests

You can call the API using GET requests. If making very long API calls, consider breaking them into shorter queries. The operational limit for a GET call is a total of 4000 characters.

## HTTP Status Codes

| Code | Description                              |
| ---- | :--------------------------------------- |
| 200  | Success!                                 |
| 401  | Unauthorized user or no available tokens |
| 404  | Syntax error                             |
| 500  | Query execution failed                   |
| 503  | Service temporarily unavailable          |

NOTE: Error details are explained in the request's response.
