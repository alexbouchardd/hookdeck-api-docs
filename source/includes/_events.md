# Events

> Endpoints

```
GET      /events
GET      /events/:id
POST     /events
POST     /events/:id/retry
PUT      /events/:id/mute
```

Events objects allow you to monitor the events of your webhooks.

## Event object

```json
{
  "id": "evt_5b3mzbxk83deakr",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "webhook_id": "web_5b3mzbxk83dcij0",
  "source_id": "src_5b3mzbxk83dciin",
  "destination_id": "des_5b3mzbxk83dciim",
  "duplicate_event_id": null,
  "attempts": 0,
  "response_status": null,
  "last_attempt_at": null,
  "next_attempt_at": null,
  "successful_at": null,
  "updated_at": "2020-03-22T18:24:01.031Z",
  "created_at": "2020-03-22T18:24:01.035Z"
}
```

| Parameter          | Type       | Default | Description                                        |
| ------------------ | ---------- | ------- | -------------------------------------------------- |
| id                 | `string`   |         | Event ID (also found in the event URL in Hookdeck) |
| team_id            | `string`   |         | Deck ID                                            |
| webhook_id         | `string`   |         | Webhook ID                                         |
| source_id          | `string`   |         | Source ID                                          |
| destination_id     | `string`   |         | Destination ID                                     |
| duplicate_event_id | `string`   | `null`    | If duplicate, shows the ID of the original event   |
| attempts           | `integer`  | 0       | Number of retries attempted                        |
| response_status    | `status`   | `null`    | Event status                                       |
| last_attempt_at    | `ISO Date` | `null`    | Last `ISO Date` a retry was attempted              |
| next_attempt_at    | `ISO Date` | `null`    | Next `ISO Date` of a scheduled retry               |
| sucessful_at       | `ISO Date` | `null`    | Date of the successful event                       |
| updated_at         | `ISO Date` |         | Last `ISO Date` the event was updated              |
| created_at         | `ISO Date` |         | Date the event was created                         |

## Retrieve all events

> The command returns JSON structured like this

```json
{
  "pagination": {
    "order_by": "created_at",
    "order_direction": "desc",
    "limit": 100,
    "after": "evt_5b3mzbxk83caj7p",
    "before": "evt_12n4ffxk8admulc"
  },
  "total_count": 3,
  "count": 3,
  "models": [
    {
      "id": "evt_12n4ffxk8admulc",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "webhook_id": "web_5b3mzbxk83dcij0",
      "source_id": "src_5b3mzbxk83dciin",
      "destination_id": "des_5b3mzbxk83dciim",
      "duplicate_event_id": null,
      "attempts": 2,
      "response_status": 500,
      "last_attempt_at": "2020-03-27T16:05:45.115Z",
      "next_attempt_at": "2020-03-27T17:06:00.000Z",
      "successful_at": null,
      "updated_at": "2020-03-27T16:05:45.249Z",
      "created_at": "2020-03-27T16:05:03.468Z"
    },
    {
      "id": "evt_5b3mzbxk83cefs5",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "webhook_id": "web_5b3mzbxk83c8qml",
      "source_id": "src_5b3mzbxk83c8qky",
      "destination_id": "des_5b3mzbxk83c8qkr",
      "duplicate_event_id": "evt_5b3mzbxk83cedro",
      "attempts": 1,
      "response_status": 500,
      "last_attempt_at": "2020-03-22T17:56:20.447Z",
      "next_attempt_at": "2020-03-22T18:56:00.000Z",
      "successful_at": null,
      "updated_at": "2020-03-22T17:56:20.540Z",
      "created_at": "2020-03-22T17:56:08.166Z"
    },
    {
      "id": "evt_5b3mzbxk83cedro",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "webhook_id": "web_5b3mzbxk83c8qml",
      "source_id": "src_5b3mzbxk83c8qky",
      "destination_id": "des_5b3mzbxk83c8qkr",
      "duplicate_event_id": null,
      "attempts": 1,
      "response_status": 500,
      "last_attempt_at": "2020-03-22T17:56:17.903Z",
      "next_attempt_at": "2020-03-22T18:56:00.000Z",
      "successful_at": null,
      "updated_at": "2020-03-22T17:56:18.006Z",
      "created_at": "2020-03-22T17:56:05.556Z"
    }
  ]
}
```

This endpoint retrieves all events.

### HTTP Request

`GET https://api.hookdeck.io/events`

## Retrieve an event

> The command returns JSON structured like this

```json
{
  "id": "evt_12n4ffxk8admulc",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "webhook_id": "web_5b3mzbxk83dcij0",
  "source_id": "src_5b3mzbxk83dciin",
  "destination_id": "des_5b3mzbxk83dciim",
  "duplicate_event_id": null,
  "attempts": 2,
  "response_status": 500,
  "last_attempt_at": "2020-03-27T16:05:45.115Z",
  "next_attempt_at": "2020-03-27T17:06:00.000Z",
  "successful_at": null,
  "updated_at": "2020-03-27T16:05:45.249Z",
  "created_at": "2020-03-27T16:05:03.468Z",
  "request": {
    "headers": {
      "host": "api-staging.hookdeck.io",
      "connection": "close",
      "test": "true",
      "content-type": "application/json",
      "time": "12",
      "authorization": "Basic MWxhamFuNHdyOXgzbjZnamlhdHVzc2FrcTN6cWZua2U1N21jZDVwcmI0ZG1kNnA4MWk6",
      "user-agent": "PostmanRuntime/7.24.0",
      "accept": "*/*",
      "cache-control": "no-cache",
      "postman-token": "85b3118d-6b69-4fb1-903c-952a1a834071",
      "accept-encoding": "gzip, deflate, br",
      "x-request-id": "168fb98f-196b-4627-841f-8fd4d1db5d88",
      "x-forwarded-for": "142.117.163.55",
      "x-forwarded-proto": "https",
      "x-forwarded-port": "443",
      "via": "1.1 vegur",
      "connect-time": "0",
      "x-request-start": "1585325103388",
      "total-route-time": "0",
      "content-length": "17"
    },
    "body": {
      "test3": true
    }
  }
}
```

This endpoint retrieves a specific event.

### HTTP Request

`GET https://api.hookdeck.io/events/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Event ID    |

## Create an event

> The command returns JSON structured like this

```json
{
"Webhook handled by https://hookdeck.io, check your event dashboard for event history https://hookdeck.io/events/evt_12n4ffxk8admulc"
}
```

This endpoint creates an event.

### HTTP Request

`POST https://api.hookdeck.io/e/:webhook_id`

Enter the event information in the body.

## Retry an event

> The command returns JSON structured like this

```json
{
  "id": "atm_12n4ffxk8aiogss",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "event_id": "evt_12n4ffxk8admulc",
  "response_status": 500,
  "successful_at": null,
  "updated_at": "2020-03-27T18:26:17.059Z",
  "created_at": "2020-03-27T18:26:16.973Z",
  "body": {}
}
```

This endpoint manually retry's an event.

### HTTP Request

`POST https://api.hookdeck.io/:id/retry`

Enter the event information in the body.

## Mute an event

> The command returns JSON structured like this

```json
{
  "id": "evt_12n4ffxk8admulc",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "webhook_id": "web_5b3mzbxk83dcij0",
  "source_id": "src_5b3mzbxk83dciin",
  "destination_id": "des_5b3mzbxk83dciim",
  "duplicate_event_id": null,
  "attempts": 4,
  "response_status": 500,
  "last_attempt_at": "2020-03-27T18:26:16.973Z",
  "next_attempt_at": null,
  "successful_at": null,
  "updated_at": "2020-03-27T18:28:27.514Z",
  "created_at": "2020-03-27T16:05:03.468Z",
  "request": {
    "headers": {
      "host": "api-staging.hookdeck.io",
      "connection": "close",
      "test": "true",
      "content-type": "application/json",
      "time": "12",
      "authorization": "Basic MWxhamFuNHdyOXgzbjZnamlhdHVzc2FrcTN6cWZua2U1N21jZDVwcmI0ZG1kNnA4MWk6",
      "user-agent": "PostmanRuntime/7.24.0",
      "accept": "*/*",
      "cache-control": "no-cache",
      "postman-token": "85b3118d-6b69-4fb1-903c-952a1a834071",
      "accept-encoding": "gzip, deflate, br",
      "x-request-id": "168fb98f-196b-4627-841f-8fd4d1db5d88",
      "x-forwarded-for": "142.117.163.55",
      "x-forwarded-proto": "https",
      "x-forwarded-port": "443",
      "via": "1.1 vegur",
      "connect-time": "0",
      "x-request-start": "1585325103388",
      "total-route-time": "0",
      "content-length": "17"
    },
    "body": {
      "test3": true
    }
  }
}
```

This endpoint mutes an event.

### HTTP Request

`POST https://api.hookdeck.io/:id/retry`

Enter the event information in the body.

<aside class="notice">
Automatic retries are cancelled. The parameter "next_attempt_at" becomes null. 
</aside>
