# API Twitter - GET Method /workers

it allows to obtain the Workers configured by the user and their data

# GET Parameters

Let's see the structure of the sample query:

```
https://twitter.trawlingweb.com/workers/?token={APIKEY}
```

## PATH Parameters

| Element  | Description                                |
| :------- | :----------------------------------------- |
| protocol | It can be **http** as **https**            |
| domain   | Address of the API twitter.trawlingweb.com |
| method   | workers                                    |

## QUERY Parameters

| Parameter | Description                                               | Default        | Example         |
| :-------- | :-------------------------------------------------------- | :------------- | :-------------- |
| token     | APIKEY to validate and access the TrawlingWeb system. Each user has their own individual and non-transferable APIKEY linked to their services and features. | Required value | ?token={APIKEY} |

# Output Response - RESPONSE

One time it is launched petition to API Twitter, this will return a structured response data:

## Data of every Worker

| Field       | Description                                            | Findable | Sortable |  Type   |    Format    |
| ----------- | ------------------------------------------------------ | :------: | :------: | :-----: | :----------: |
| id          | Identificate id of the Worker                          |    No    |    No    | String  |              |
| type        | Type of Worker (facebook, instagram, twitter)          |    No    |    No    | String  |              |
| description | Established description by the user                    |    No    |    No    | String  |              |
| words       | Search words.                                          |    No    |    No    | String  |              |
| counter     | Number of stored publications                          |    No    |    No    | Integer |              |
| created_at  | Creation date of the Worker                            |    No    |    No    |  Date   | ISO 8601-UTC |
| status      | Status of the activity Worker ( 1 running , 0 stoped ) |    No    |    No    | Integer |              |

## General data

| Field       | Description                 | Findable | Sortable |  Type   | Format |
| ----------- | --------------------------- | :------: | :------: | :-----: | :----: |
| workersLeft | Number of available Workers |    No    |    No    | Integer |        |
| limit       | Maximum number of Workers   |    No    |    No    | Integer |        |

## Example of response in json format:

```json
"response" : {
    "workers" : [{
            "id" : "...",
            "type" : "...",
            "description" : "...",
            "words" : "...",
            "counter" : "...",
            "created_at" : "...",
            "status" : "..."
    }],
    "workersLeft" : "...",
    "limit" : "..."
}
```
# Contact

If you have any questions, need assistance, want to hire or expand your services, please contact us.

**Technical Support (SAT):**
- [Email SAT](mailto:support@trawlingweb.com)
- [Official Documentation](https://docs.trawlingweb.com)

**Administrative Support (SAC):**
- [Email SAC](mailto:gestion@trawlingweb.com)

**Sales Support:**
- [Email Sales](mailto:sales@trawlingweb.com)
