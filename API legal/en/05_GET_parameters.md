# Legal API - GET Parameters

## Query Method

Let's break down the structure of the example query:

```
https://law.trawlingweb.com/?token={APIKEY}&q="ley"%20AND%20"economía"&ts=1518472804000
```

## Here, we can identify:

| Element    | Description                            |
| :--------- | :------------------------------------- |
| Protocol   | It can be either **http** or **https** |
| Domain     | The address of the TrawlingWeb API     |
| Parameters | Query parameters                       |

## Elements specifying the information desired and the format in which it should be received:

| Parameter | Description                                                                                                                                                                  | Default                                          | Example                      |
| :-------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------- | :--------------------------- |
| token     | Client's access APIKEY to the TrawlingWeb system.                                                                                                                            | Mandatory value                                  | ?token={APIKEY}              |
| q         | Expression constructed with keywords or phrases that configure search filters. Allows combinations with different filter types using the boolean operators AND, OR, and NOT. | Returns all publications by default              | &q="domain=lavanguardia.com" |
| ts        | This is the initial time delimiter. Unix Time format in milliseconds                                                                                                         | Delimits to 1 month in the past from the request | &ts=1518472804000            |
