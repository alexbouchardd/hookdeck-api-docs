# Sources

> Endpoints

```
GET      /sources
GET      /sources/:id
POST     /sources
PUT      /sources/:id
PUT      /sources/:id/archive
PUT      /sources/:id/unarchive
```

Source objects allow you to define the third party sending the webhook.

## Source object

```json
{
  "id": "src_1b69dxk87s0g4k",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "Intercom Production",
  "alias": "intercom-prod",
  "description": "Our intercom production environement",
  "archived_at": "2020-03-25T20:46:26.742Z",
  "updated_at": "2020-03-25T20:46:26.742Z",
  "created_at": "2020-03-25T20:24:14.069Z"
}
```

| Parameter   | Type     | Default | Description                                |
| ----------- | -------- | ------- | ------------------------------------------ |
| id          | `string` |         | Source ID                                  |
| team_id     | `string` |         | Deck ID                                    |
| label       | `string` |         | Name of the source                         |
| alias       | `string` | `null`  | A unique, human friendly id for the source |
| description | `string` | `null`  | Description of the source                  |
| archived_at | `date`   | `null`  | Date the source was archived               |
| updated_at  | `date`   |         | ISO Last `ISO Date` the source was updated |
| created_at  | `date`   |         | ISO Date the source was created            |

## Retrieve all sources

> The command returns JSON structured like this

```json
{
  "pagination": {
    "order_by": "created_at",
    "order_direction": "desc",
    "limit": 100,
    "after": "src_5b3mzbxk83c8qky",
    "before": "src_5b3mzbxk83dciin"
  },
  "total_count": 2,
  "count": 2,
  "models": [
    {
      "id": "src_5b3mzbxk83dciin",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "label": "Stripe",
      "alias": null,
      "description": null,
      "archived_at": null,
      "updated_at": "2020-03-22T18:22:38.012Z",
      "created_at": "2020-03-22T18:22:38.015Z"
    },
    {
      "id": "src_5b3mzbxk83c8qky",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "label": "Shopify",
      "alias": null,
      "description": null,
      "archived_at": null,
      "updated_at": "2020-03-22T17:51:42.229Z",
      "created_at": "2020-03-22T17:51:42.231Z"
    }
  ]
}
```

This endpoint retrieves all unarchived sources.

### HTTP Request

`GET https://api.hookdeck.io/sources`

### Query Parameter

| Parameter | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| archived  | `boolean` | Include the archived resources in response |

## Retrieve a source

> The command returns JSON structured like this

```json
{
  "id": "src_5b3mzbxk83dciin",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "Stripe",
  "alias": null,
  "description": null,
  "archived_at": null,
  "updated_at": "2020-03-22T18:22:38.012Z",
  "created_at": "2020-03-22T18:22:38.015Z"
}
```

This endpoint retrieves a specific source.

### HTTP Request

`GET https://api.hookdeck.io/sources/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Source ID   |

## Create a source

> The command returns JSON structured like this

```json
{
  "id": "src_1b69dxk87s0g4k",
  "label": "Intercom",
  "description": null,
  "alias": null,
  "team_id": "tm_5b3mzbxk83c0k7i",
  "created_at": "2020-03-25T20:59:30.127Z"
}
```

This endpoint creates a source.

### HTTP Request

`POST https://api.hookdeck.io/sources/`

| Parameter   | Type     | Description                                |
| ----------- | -------- | ------------------------------------------ |
| label       | `string` | Name of the source                         |
| alias       | `string` | A unique, human friendly id for the source |
| description | `string` | Description of the source                  |

## Update a source

> The command returns JSON structured like this

```json
{
  "id": "src_1b69dxk87s0g4k",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "Intercom",
  "alias": null,
  "description": "Our intercom dev environement",
  "archived_at": null,
  "updated_at": "2020-03-25T20:43:20.880Z",
  "created_at": "2020-03-25T20:24:14.069Z"
}
```

This endpoint updates a source.

### HTTP Request

`PUT https://api.hookdeck.io/sources/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Source ID   |

### Body Parameters

| Parameter   | Type     | Description                                |
| ----------- | -------- | ------------------------------------------ |
| label       | `string` | Name of the source                         |
| alias       | `string` | A unique, human friendly id for the source |
| description | `string` | Description of the source                  |

## Archive a source

> The command returns JSON structured like this

```json
{
  "id": "src_1b69dxk87s0g4k",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "Intercom",
  "alias": null,
  "description": "Our intercom production environement",
  "archived_at": "2020-03-25T20:46:26.742Z",
  "updated_at": "2020-03-25T20:46:26.742Z",
  "created_at": "2020-03-25T20:24:14.069Z"
}
```

This endpoint archives a source.

### HTTP Request

`PUT https://api.hookdeck.io/sources/:id/archive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Source ID   |

<aside class="notice">
The parameter `archived_at`is set to the current ISO timestamp
</aside>

## Unarchive a source

> The command returns JSON structured like this

```json
{
  "id": "src_1b69dxk87s0g4k",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "Intercom",
  "alias": null,
  "description": "Our intercom production environement",
  "archived_at": null,
  "updated_at": "2020-03-25T21:03:29.125Z",
  "created_at": "2020-03-25T20:24:14.069Z"
}
```

This endpoint unarchives a source.

### HTTP Request

`PUT https://api.hookdeck.io/sources/:id/unarchive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Source ID   |

<aside class="notice">
The parameter `archived_at`becomes null
</aside>
