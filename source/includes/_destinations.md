# Destinations

> Endpoints

```
GET      /destinations
GET      /destinations/:id
POST     /destinations
PUT      /destinations/:id
PUT      /destinations/:id/archive
PUT      /destinations/:id/unarchive
```

Destination objects allows you to receive webhooks to your systems.

## Destination object

```json
{
  "id": "des_5b3mzbxk83dciim",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "My API 2",
  "alias": null,
  "description": "Our shopify dev environement",
  "url": "https://example.com/webhook",
  "archived_at": null,
  "updated_at": "2020-03-26T17:15:31.079Z",
  "created_at": "2020-03-22T18:22:38.015Z"
}
```

| Parameter   | Type       | Default | Description                                 |
| ----------- | ---------- | ------- | ------------------------------------------- |
| id          | `string`   |         | Destination ID                              |
| team_id     | `string`   |         | Deck ID                                     |
| label       | `string`   |         | Name of the destination                     |
| alias       | `string`   | `null`  | Alternate name for the destination          |
| description | `string`   | `null`  | Description of the destination              |
| url         | `url`      |         | Endpoint of the destination                 |
| archived_at | `ISO Date` | `null`  | Date the destination was archived           |
| updated_at  | `ISO Date` |         | Last `ISO Date` the destination was updated |
| created_at  | `ISO Date` |         | Date the destination was created            |

## Retrieve all destinations

> The command returns JSON structured like this

```json
{
  "pagination": {
    "order_by": "created_at",
    "dir": "desc",
    "limit": 100,
    "next": "des_5b3mzbxk83c8qkr",
    "prev": "des_5b3mzbxk83dciim"
  },
  "total_count": 2,
  "count": 2,
  "models": [
    {
      "id": "des_5b3mzbxk83dciim",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "label": "My API 2",
      "alias": null,
      "description": "Our shopify dev environement",
      "url": "https://example.com/webhook",
      "archived_at": null,
      "updated_at": "2020-03-26T17:15:31.079Z",
      "created_at": "2020-03-22T18:22:38.015Z"
    },
    {
      "id": "des_5b3mzbxk83c8qkr",
      "team_id": "tm_5b3mzbxk83c0k7i",
      "label": "My API",
      "alias": null,
      "description": null,
      "url": "https://example.com/webhook",
      "archived_at": null,
      "updated_at": "2020-03-22T17:51:42.228Z",
      "created_at": "2020-03-22T17:51:42.231Z"
    }
  ]
}
```

This endpoint retrieves all destinations.

### HTTP Request

`GET https://api.hookdeck.io/destinations`

### Query Parameter

| Parameter | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| archived  | `boolean` | Include the archived resources in response |

## Retrieve a destination

> The command returns JSON structured like this

```json
{
  "id": "des_5b3mzbxk83c8qkr",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "My API",
  "alias": null,
  "description": null,
  "url": "https://example.com/webhook",
  "archived_at": null,
  "updated_at": "2020-03-22T17:51:42.228Z",
  "created_at": "2020-03-22T17:51:42.231Z"
}
```

This endpoint retrieves a specific destination.

### HTTP Request

`GET https://api.hookdeck.io/destinations/:id`

### URL Parameter

| Parameter | Description    |
| --------- | -------------- |
| id        | Destination ID |

## Create a destination

> The command returns JSON structured like this

```json
{
  "id": "des_1b69dxk890yel0",
  "label": "My API 3",
  "description": null,
  "alias": null,
  "url": "https://example.com/webhook",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "created_at": "2020-03-26T17:22:21.398Z"
}
```

This endpoint creates a destination.

### HTTP Request

`POST https://api.hookdeck.io/destination/`

| Parameter   | Type     | Description                        |
| ----------- | -------- | ---------------------------------- |
| label       | `string` | Name of the destination            |
| alias       | `string` | Alternate name for the destination |
| description | `string` | Description of the destination     |
| url         | `url`    | Endpoint of the destination        |

## Update a destination

> The command returns JSON structured like this

```json
{
  "id": "des_1b69dxk890yel0",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "My API 3",
  "alias": null,
  "description": "Our Intercom dev environement",
  "url": "https://example.com/webhook",
  "archived_at": null,
  "updated_at": "2020-03-26T17:24:15.249Z",
  "created_at": "2020-03-26T17:22:21.398Z"
}
```

This endpoint updates a destination.

### HTTP Request

`PUT https://api.hookdeck.io/destination/:id`

### URL Parameter

| Parameter | Description    |
| --------- | -------------- |
| id        | Destination ID |

### Body Parameters

| Parameter   | Type     | Description                        |
| ----------- | -------- | ---------------------------------- |
| label       | `string` | Name of the destination            |
| alias       | `string` | Alternate name for the destination |
| description | `string` | Description of the destination     |
| url         | `url`    | Endpoint of the destination        |

## Archive a destination

> The command returns JSON structured like this

```json
{
  "id": "des_1b69dxk890yel0",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "My API 3",
  "alias": null,
  "description": "Our Intercom dev environement",
  "url": "https://example.com/webhook",
  "archived_at": "2020-03-26T17:27:19.529Z",
  "updated_at": "2020-03-26T17:27:19.530Z",
  "created_at": "2020-03-26T17:22:21.398Z"
}
```

This endpoint archives a destination.

### HTTP Request

`PUT https://api.hookdeck.io/destination/:id/archive`

### URL Parameter

| Parameter | Description    |
| --------- | -------------- |
| id        | Destination ID |

<aside class="notice">
The parameter `archived_at`is updated
</aside>

## Unarchive a destination

> The command returns JSON structured like this

```json
{
  "id": "des_1b69dxk890yel0",
  "team_id": "tm_5b3mzbxk83c0k7i",
  "label": "My API 3",
  "alias": null,
  "description": "Our Intercom dev environement",
  "url": "https://example.com/webhook",
  "archived_at": null,
  "updated_at": "2020-03-26T17:28:15.207Z",
  "created_at": "2020-03-26T17:22:21.398Z"
}
```

This endpoint unarchives a destination.

### HTTP Request

`PUT https://api.hookdeck.io/destination/:id/unarchive`

### URL Parameter

| Parameter | Description    |
| --------- | -------------- |
| id        | Destination ID |

<aside class="notice">
The parameter `archived_at` is set to null
</aside>
