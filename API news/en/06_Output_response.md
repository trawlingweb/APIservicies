# API NEWS & BLOGS - Output response

Once API request has been launched, API will return a file to client as a response that includes two sets of data:

## News data

| Field           | Description                                                              | Findable | Sortable |   Type    |           Format            |
| --------------- | ------------------------------------------------------------------------ | :------: | :------: | :-------: | :-------------------------: |
| id              | Identification code of each crawled publication assigned by Trawlingweb. |    No    |    No    |  String   |                             |
| title           | Title of the publication.                                                |    Si    |    No    |  String   |                             |
| text            | Body text of the publication.                                            |    Si    |    No    |  String   |                             |
| published       | Publication date-time.                                                   |    Si    |    Si    | Date-Time |        ISO 8601-UTC         |
| crawled         | Crawl date-time. Time Zone = GMT +1                                      |    Si    |    Si    |  Integer  | UNIX Timestamp milliseconds |
| url             | Website address of the publication.                                      |    No    |    No    |  String   |                             |
| author          | Author of the publication.                                               |    Si    |    No    |  String   |                             |
| language        | Language of the publication.                                             |    Si    |    No    |  String   |          ISO 639-1          |
| domain          | Web domain of publication.                                               |    Si    |    No    |  String   |                             |
| site            | Web site of publication.                                                 |    Si    |    No    |  String   |                             |
| site_type       | Type of Website (news, blogs, discussions and general)                   |    Si    |    No    |  String   |                             |
| site_language   | Website language.                                                        |    Si    |    No    |  String   |          ISO 639-1          |
| site_country    | Website country.                                                         |    Si    |    No    |  String   |         ISO 3166-2          |
| site_region     | Website region.                                                          |    Si    |    No    |  String   |        ISO 3166-2:ES        |
| site_section    | Website section of the publication.                                      |    No    |    No    |  String   |                             |
| section         | Section of publication.                                                  |    No    |    No    |  String   |                             |
| value           | Estimated economic value.                                                |    No    |    No    |   Float   |                             |
| rank            | Domain ranking.                                                          |    No    |    No    |  Integer  |                             |
| unique_visitors | Amount of estimated unique visitors.                                     |    No    |    No    |  Integer  |                             |

## Request data

| Data         | Description                                                                                                                     |  Type   |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------ | :-----: |
| requestLeft  | Number of pending queries to finish service subscription.                                                                       | Integer |
| totalResults | TNumber of publications found by the search                                                                                     | Integer |
| restResults  | Number of publications pending to be served                                                                                     | Integer |
| next         | Automatic generated link to receive the next response file. Remember trawlingweb system serves required data in 100 rows files. | String  |

### JSON format response:

```json
"response" : {
    "data" : [{
        "id" : "...",
        "title" : "...",
        "text" : "...",
        "published" : "...",
        "crawled" : "...",
        "url" : "...",
        "author" : "...",
        "language" : "...",
        "domain" : "...",
        "site" : "...",
        "site_type" : "...",
        "site_language" : "...",
        "site_country" : "...",
        "site_region" : "...",
        "site_section" : "...",
        "section" : "...",
        "value" : "...",
        "rank" : "...",
        "unique_visitors" : "..."
    }],
    "requestLeft" : "...",
    "totalResults" : "...",
    "restResults" : "...",
    "next" : "..."
}
```
### Below is an example of output from an API call. This output includes information about the remaining results, the total number of results, and the URL to obtain the next results.

```
requestLeft	9999999
totalResults	295404987
restResults	295404887
next	"http://api.trawlingweb.com/?token=0000000000000000000000000000&q=casa&ts=1517443760316&tsi=1524818189854"

```

# **Contact Us:**
If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
* [SAT Email](mailto:support@trawlingweb.com)
* [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
* [SAC Email](mailto:gestion@trawlingweb.com)

**Sales Support (Sales):**
* [Sales Email](mailto:sales@trawlingweb.com)