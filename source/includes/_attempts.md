# Attempts

> Endpoints

```
GET      /attempts
GET      /attempts/:id
```

Attempt objects allow you to monitor the attempts of your events.

## Attempt object

```json
{
  "id": "atm_12n4ffxk8adnqqj",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "event_id": "evt_12n4ffxk8admulc",
  "response_status": 500,
  "successful_at": null,
  "updated_at": "2020-03-27T16:05:45.240Z",
  "created_at": "2020-03-27T16:05:45.115Z",
  "body": {}
}
```

| Parameter    | Type       | Default | Description                           |
| ------------ | ---------- | ------- | ------------------------------------- |
| id           | `string`   |         | Attempt ID                            |
| team_id      | `string`   |         | Deck ID                               |
| event_id     | `string`   |         | Event ID                              |
| sucessful_at | `ISO Date` | `null`    | Date of the successful event        |
| updated_at   | `ISO Date` |         | Last `ISO Date` the event was updated |
| created_at   | `ISO Date` |         | Date the event was created            |

## Retrieve all attempts

> The command returns JSON structured like this

```json
    "pagination": {
        "order_by": "created_at",
        "order_direction": "desc",
        "limit": 100,
        "after": "atm_5b3mzbxk83cenaj",
        "before": "atm_12n4ffxk8adnqqj"
    },
    "total_count": 4,
    "count": 4,
    "models": [
        {
            "id": "atm_12n4ffxk8adnqqj",
            "team_id": "tm_5b3mzbxk83c0k7i",
            "event_id": "evt_12n4ffxk8admulc",
            "response_status": 500,
            "successful_at": null,
            "updated_at": "2020-03-27T16:05:45.240Z",
            "created_at": "2020-03-27T16:05:45.115Z"
        },
        {
            "id": "atm_12n4ffxk8adnbk0",
            "team_id": "tm_5b3mzbxk83c0k7i",
            "event_id": "evt_12n4ffxk8admulc",
            "response_status": 500,
            "successful_at": null,
            "updated_at": "2020-03-27T16:05:25.561Z",
            "created_at": "2020-03-27T16:05:25.443Z"
        },
        {
            "id": "atm_5b3mzbxk83cep9b",
            "team_id": "tm_5b3mzbxk83c0k7i",
            "event_id": "evt_5b3mzbxk83cefs5",
            "response_status": 500,
            "successful_at": null,
            "updated_at": "2020-03-22T17:56:20.530Z",
            "created_at": "2020-03-22T17:56:20.447Z"
        },
        {
            "id": "atm_5b3mzbxk83cenaj",
            "team_id": "tm_5b3mzbxk83c0k7i",
            "event_id": "evt_5b3mzbxk83cedro",
            "response_status": 500,
            "successful_at": null,
            "updated_at": "2020-03-22T17:56:17.991Z",
            "created_at": "2020-03-22T17:56:17.903Z"
        }
    ]
}
```

This endpoint retrieves all attempts.

### HTTP Request

`GET https://api.hookdeck.io/attempts`

## Retrieve an attempt

> The command returns JSON structured like this

```json
{
  "id": "atm_12n4ffxk8adnbk0",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "event_id": "evt_12n4ffxk8admulc",
  "response_status": 500,
  "successful_at": null,
  "updated_at": "2020-03-27T16:05:25.561Z",
  "created_at": "2020-03-27T16:05:25.443Z",
  "body": {}
}
```

This endpoint retrieves a specific attempt.

The attempt with also include the attempt response `body` in `json`.

### HTTP Request

`GET https://api.hookdeck.io/attempt/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Attempt ID  |
