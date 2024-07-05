# Legal API - Best Practices

To use the API, you need to make a request to an endpoint URL with your private access token.

## Data Integrity

Each API request can return a maximum of 100 messages that match your query. However, there may be many more results that match your filter parameters. To consume all the data, you must continue making calls to the URL specified in the **next** parameter of the output of each request.

## Example Output

```
requestLeft	9999999
totalResults	295404987
restResults	295404887
next	"http://law.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&q=Europa&ts=1517443760316&tsi=1524818189854"
}
```

## Pagination

Depending on the total number of results (totalResults), the API will automatically determine which timestamp values are necessary so that the URL in the next parameter includes the next set of results. Both $ts and $tsi are timestamps (Unix Microtime).
