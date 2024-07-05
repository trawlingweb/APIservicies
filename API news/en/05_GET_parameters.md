# API NEWS & BLOGS - GET Parameters

Let's see the query structure with an example:

```
https://api.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&q="messi"%20AND%20"Barcelona"&ts=1518472804000&size=100
```

## Query elements

| Element    | Description                      |
| :--------- | :------------------------------- |
| protocol   | **http** and **https** available |
| domain     | api.trawlingweb.com API address  |
| parameters | Query parameters                 |

## Query configuration parameters

We combine this elements to get a high accurate searching configuration of the filters and reduce the amount of data to retrieve in order to obtain only wanted information.

| Parameter | Description                                                                                                                                                                                          | Default                           | Example                      |
| :-------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------- | ---------------------------- |
| ?token    | Client API key to get access at the Trawlingweb system                                                                                                                                               | Required                          | token=xxxxxx                 |
| q         | Query expression with searching keywords and setting filters. Combinations of filters with booleans operators are allowed.                                                                           | Filters off by default            | &q="domain=lavanguardia.com" |
| ts        | Initial date-time limit reference in Unix time (miliseconds)                                                                                                                                         | 3 months before from query moment | ts=1518472804000             |
| size      | Amount of rows (publications) per page. TrawlingWeb serves required data in pages with a maximum amount of 100 rows. Each page is an effective response. Set up the amount of rows between 1 and 100 | 100 rows by default               | size=40                      |
| format    | Set up the response file format. Formats available: JSON and XML                                                                                                                                     | JSON file format by default       | format=xml                   |
| sort      | It's possible to receive the publication rows sorted by publishing date or crawling date.                                                                                                            | Crawled date by default           | sort=published               |
| order     | Set up the order in ascending (from older news to newer) or descending (from newer news to older)                                                                                                    | Ascending by default              | order=desc                   |
