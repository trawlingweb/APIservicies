# API Twitter - POST Method /create

it allows to create new Workers with their words.

# POST Parameters

Let's see the structure of the sample query:

```
https://twitter.trawlingweb.com/create/?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                |
| :------- | :----------------------------------------- |
| protocol | It can be **http** as **https**            |
| domain   | Address of the API twitter.trawlingweb.com |
| method   | create                                     |

## Query Parameters

| Parameter | Description                                               | Default        | Example         |
| :-------- | :-------------------------------------------------------- | :------------- | :-------------- |
| token     | APIKEY access of the client to the system of TrawlingWeb. | Required value | ?token={APIKEY} |

## BODY Parameters

| Parameter   | Description                              | Default        | Limits                                                   |
| :---------- | :--------------------------------------- | :------------- | :------------------------------------------------------- |
| description | Description that should have the Worker. | Required value | String not superior to 200 characters                    |
| words       | Search words.                            | Required value | The number of words should not exceed the accorded limit |

# Output Response - RESPONSE

One time it is launched petition to API Twitter, this will return a structured response data:

## Status 200 - Return Data

| Field  | Description                               |  Type  |
| ------ | ----------------------------------------- | :----: |
| worker | Identifier of the created Worker.         | String |
| msg    | Description indicating successfull action | String |

## Example of response in json format:

```json
"response" : {
    "worker" : "...",
    "msg" : "..."
}
```

## Status 400 - Return Data

| Field | Description       |  Type  |
| ----- | ----------------- | :----: |
| error | Error description | String |

## Example of response in json format:

```json
"response" : {
    "error" : "..."
}
```

# Workers characteristics

We can define a Worker as a capture unit and independent storage.

The user creates and defines what search terms has every Worker and he can do it directly in the dashboard ( https://dashboard.trawlingweb.com/workers) or using this method.

When creating a Worker it begins their deployment to begin their capture work, structuring and storage. This deployment may take an hour.

Every Worker has an independent database and a specific duplicate results control.

## Characteristics of the words defined by the user

| Type           | Description                                                                  | Example          |
| -------------- | :--------------------------------------------------------------------------- | :--------------- |
| hashtag        | Referenced terms with the hashtag #                                          | #house           |
| At             | Referenced users with the at @                                               | @pepe            |
| Simple string  | Words with alphanumeric terms without special characters                     | Studio54         |
| Complex string | Words with alphanumeric terms without special characters separated by spaces | Casa Blanca 2019 |

## Reserved characters in search words

> The reserved characters are: + - = & | > < ! ¡ () {} [] ^ " ~ \* ¿ ?: \ / ' -
