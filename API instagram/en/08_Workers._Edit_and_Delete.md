# API Instagram - GET Method /delete

If a worker no longer serves you, you can take and leave space to create a new one.

# GET Parameters

Let's see the structure of the sample query:

```
https://instagram.trawlingweb.com/delete/xxxxxxxxxxxxx?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                  |
| :------- | :------------------------------------------- |
| protocol | It can be **http** as **https**              |
| domain   | Address of the API instagram.trawlingweb.com |
| method   | delete                                       |
| id       | Identifier of the Worker to delete           |

## QUERY Parameters

| Parameter | Description                                               | Default        | Example         |
| :-------- | :-------------------------------------------------------- | :------------- | :-------------- |
| token     | APIKEY access of the client to the system of TrawlingWeb. | Required value | ?token={APIKEY} |

# Output Response - RESPONSE

One time it is launched petition to API Instagram, this will return a structured response data:

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

Every Worker store the results during 30 days.

The user can remove a specific Worker. This remove implies the destruction of the worker configuration and the database associate with it.
