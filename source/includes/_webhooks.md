# Webhooks

## Get All Webhooks

```shell
curl "https://api.hoockdeck.io/webhooks"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "pagination": {
    "order_by": "created_at",
    "order_direction": "desc",
    "limit": 100,
    "after": "web_2urj7h9puxk6obro3x",
    "before": "web_2urj7h9puxk6obuf6i"
  },
  "total_count": 3,
  "count": 3,
  "models": [
    {
      "id": "web_2urj7h9puxk6obuf6i",
      "label": "Intercom to Customer Service",
      "team_id": "tm_14ac3180dk5dbw5zo",
      "archived_at": null,
      "updated_at": "2020-02-16T01:04:19.291Z",
      "created_at": "2020-02-16T01:04:19.290Z",
      "destination": {
        "id": "des_2urj7h9mn7k6obnksu",
        "team_id": "tm_14ac3180dk5dbw5zo",
        "label": "Customer Service",
        "description": null,
        "url": "https://hoockdeck.io/test",
        "archived_at": null,
        "updated_at": "2020-02-16T00:58:59.983Z",
        "created_at": "2020-02-16T00:58:59.983Z"
      },
      "source": {
        "id": "src_2urj7h9mn7k6obmg5c",
        "team_id": "tm_14ac3180dk5dbw5zo",
        "label": "Intercom",
        "description": null,
        "archived_at": null,
        "updated_at": "2020-02-16T00:58:07.298Z",
        "created_at": "2020-02-16T00:58:07.296Z"
      },
      "ruleset": {
        "id": "rls_k0wayflksk5lhyv64",
        "team_id": "tm_14ac3180dk5dbw5zo",
        "label": "Default Ruleset",
        "description": "Production ruleset",
        "retries_count": 10,
        "retries_interval": 10000,
        "notify_by": null,
        "notify_treshold": null,
        "idempotent": true,
        "archived_at": null,
        "updated_at": "2020-01-19T20:54:19.806Z",
        "created_at": "2020-01-19T20:52:43.468Z"
      }
    },
    ...
  ]
}
```

This endpoint retrieves all your team webhooks.

### HTTP Request

`GET https://api.hoockdeck.io/webhooks`

### Query Parameters

| Parameter      | Default   | Description                                  |
| -------------- | --------- | -------------------------------------------- |
| archived       | false     | Return archived webhooks                     |
| source_id      | undefined | Return webhooks using a specific source      |
| destination_id | undefined | Return webhooks using a specific destination |
| ruleset_id     | undefined | Return webhooks using a specific ruleset     |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

> The above command returns JSON structured like this:

```json
{
  "id": "web_2urj7h9puxk6obuf6i",
  "label": "Intercom to Customer Service",
  "team_id": "tm_14ac3180dk5dbw5zo",
  "archived_at": null,
  "updated_at": "2020-02-16T01:04:19.291Z",
  "created_at": "2020-02-16T01:04:19.290Z",
  "destination": {
    "id": "des_2urj7h9mn7k6obnksu",
    "team_id": "tm_14ac3180dk5dbw5zo",
    "label": "Customer Service",
    "description": null,
    "url": "https://hoockdeck.io/test",
    "archived_at": null,
    "updated_at": "2020-02-16T00:58:59.983Z",
    "created_at": "2020-02-16T00:58:59.983Z"
  },
  "source": {
    "id": "src_2urj7h9mn7k6obmg5c",
    "team_id": "tm_14ac3180dk5dbw5zo",
    "label": "Intercom",
    "description": null,
    "archived_at": null,
    "updated_at": "2020-02-16T00:58:07.298Z",
    "created_at": "2020-02-16T00:58:07.296Z"
  },
  "ruleset": {
    "id": "rls_k0wayflksk5lhyv64",
    "team_id": "tm_14ac3180dk5dbw5zo",
    "label": "Default Ruleset",
    "description": "Production ruleset",
    "retries_count": 10,
    "retries_interval": 10000,
    "notify_by": null,
    "notify_treshold": null,
    "idempotent": true,
    "archived_at": null,
    "updated_at": "2020-01-19T20:54:19.806Z",
    "created_at": "2020-01-19T20:52:43.468Z"
  }
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.hoockdeck.io/webhooks/:id`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "https://api.hoockdeck.io/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE https://api.hoockdeck.io//kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
