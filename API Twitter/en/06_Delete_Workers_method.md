# API Twitter - GET Method /delete

If a Worker no longer serves you, you can take and leave space to create a new one.

# GET Parameters

Let's see the structure of the sample query:

```
https://twitter.trawlingweb.com/delete/{WORKERID}?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                                              | Default        | Example      |
| :------- | :----------------------------------------------------------------------- | :------------- | :----------- |
| protocol | It can be **http** as **https**                                          |                |              |
| domain   | Address of the API twitter.trawlingweb.com                               |                |              |
| method   | delete                                                                   |                |              |
| workerid | WORKERID access to the database of the worker in the TrawlingWeb system. | Required Value | /{WORKERID}? |

## QUERY Parameters

| Parameter | Description                                               | Default        | Example         |
| :-------- | :-------------------------------------------------------- | :------------- | :-------------- |
| token     | APIKEY access of the client to the system of TrawlingWeb. | Required value | ?token={APIKEY} |

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

Every Worker store the results during 30 days.

The user can remove a specific Worker. This remove implies the destruction of the worker configuration and the database associate with it.
