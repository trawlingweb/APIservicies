# API NEWS & BLOGS - Best practices

To get access to the Trawlingweb API NEWS & BLOGS, a calling to an URL endpoint with a private access token is needed. This URL call can be generated with the Constructor Request (a connection to API is required).

## Data Integrity

Each API request can return a maximum of 100 messages matching your query. However, there may be many more results that match your filter parameters. To consume all the data, you must continue making calls to the URL indicated in the parameter **next** of the output of each request.

## Outcome example

```
{
"requestLeft"  :    "9999999"
"totalResults" : 	"295404987"
"restResults"  : 	"295404887"
"next"         :	"http://api.trawlingweb.com/?token=XXXXXXXXXXXXXXXXXXXXX&q=language%3Aen&ts=1517443760316&tsi=1524818189854"
}
```

## Pagination

In function of the sorting order, the URL "next" address includes the **&ts** and **&tsi** values with an adapted behaviour to the sorted results. These values are timestamp (UnixMicrotime).

## Pagination modes

There are 4 pagination modes:

#### &order=crawled &sort=asc &size=100 (Default mode)

News are ordered by date of capture (crawled) from older to newer. In the "next" URL, &ts jumps from 100 results to &tsi.

#### &order=crawled &sort=desc &size=100

News are ordered by date of capture (crawled) from newer to older. In the "next" URL, &tsi jumps from 100 results to &ts.

#### &order=published &sort=asc &size=100

News are ordered by date of published (published) from older to newer. In the "next" URL, &ts jumps from 100 results to &tsi.

#### &order=published &sort=desc &size=100

News are ordered by date of published (published) from newer to older. In the "next" URL, &tsi jumps from 100 results to &ts.


## Periodic Maintenance of Media Sources

Periodic maintenance of media sources is constant and core at TrawlingWeb, involving a comprehensive reevaluation of each source, often incorporating new sections to scrape previously uncaptured content. Having the capture dates (`crawled`) and publication dates (`published`) allows these updates to be efficiently managed.

When adding new media sources to our coverage, we frequently include their history by performing an initial deep scrape of all their sections. Again, the capture dates (`crawled`) and publication dates (`published`) facilitate this process.

Certain sections of media sources, in addition to chronological content, display non-chronological content (such as rankings or related news), which we also capture.

### Considerations

- **Scraping Frequency**: The frequency of scraping a media source is determined by the client's needs, functional requirements, the volume of news, and the media's publication frequency.
- **Date Differentiation**: Clearly distinguishing the capture date (`crawled`) from the publication date (`published`) allows clients to decide which news items to incorporate.
- **Content Delivery Philosophy**: Our philosophy is to deliver all captured news, leaving the decision on how to utilize this content to the clients.

### Delivered and Discarded News

- **Delivered News**: All captured news items are delivered to the client.
- **Discarded News**: Clients have the option to discard news items based on their specific criteria and needs.

## Tips on the Use of `published` and `crawled` Dates

Trawlingweb provides two dates for each news item: `published` (publication date) and `crawled` (capture date). This is crucial because, when incorporating new sections, the system may detect as new news items that were published days or even months ago.

It can also happen that media sources modify their publication systems, causing the appearance of old news due to errors or SEO strategies. To avoid or control these occurrences, we recommend that clients implement security rules in their systems.

### Tips on Rules to Ensure Proper Use of Dates:

- **Date Filters**: Establish filters to ignore news with very old publication dates.
- **Relevance Rules**: Create criteria that determine the relevance of news based on their publication and capture dates.
- **Change Monitoring**: Monitor changes in the publication systems of media sources to adjust capture and processing rules accordingly.
- **Alerts and Notifications**: Set up alerts to detect and notify the appearance of old news, allowing for manual review if necessary.

Implementing these measures helps our clients maintain the integrity and relevance of the data captured by TrawlingWeb.