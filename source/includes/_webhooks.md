# Webhooks

> Endpoints

```
GET      /webhooks
GET      /webhooks/:id
POST     /webhooks
PUT      /webhooks/:id
PUT      /webhooks/:id/archive
PUT      /webhooks/:id/unarchive
```

Webhook objects allows you to proxy a source, a destination and a ruleset.

## Webhook object

```json
{
  "id": "web_5b3mzbxk83c8qml",
  "label": "Shopify to My API",
  "alias": null,
  "team_id": "tm_5b3mzbxk83c0k7i",
  "archived_at": null,
  "updated_at": "2020-03-22T17:51:42.286Z",
  "created_at": "2020-03-22T17:51:42.290Z"
}
```

| Parameter   | Type       | Default | Description                             |
| ----------- | ---------- | ------- | --------------------------------------- |
| id          | `string`   |         | Webhook ID                              |
| label       | `string`   |         | Name of the webhook                     |
| alias       | `string`   | `null`  | Alternate name for the webhook          |  | team_id | `string` |  | Deck ID |
| archived_at | `ISO Date` | `null`  | Date the webhook was archived           |
| updated_at  | `ISO Date` |         | Last `ISO Date` the webhook was updated |
| created_at  | `ISO Date` |         | Date the webhook was created            |

## Retrieve all webhooks

> The command returns JSON structured like this

```json
{
  "pagination": {
    "order_by": "created_at",
    "order_direction": "desc",
    "limit": 100,
    "after": "web_5b3mzbxk83c8qml",
    "before": "web_5b3mzbxk83dcij0"
  },
  "total_count": 1,
  "count": 1,
  "models": [
    {
      "id": "web_5b3mzbxk83c8qml",
      "label": "Shopify to My API",
      "alias": null,
      "team_id": "tm_5b3mzbxk83c0k7i",
      "archived_at": null,
      "updated_at": "2020-03-22T17:51:42.286Z",
      "created_at": "2020-03-22T17:51:42.290Z",
      "source": {
        "id": "src_5b3mzbxk83c8qky",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Shopify",
        "alias": null,
        "description": null,
        "archived_at": null,
        "updated_at": "2020-03-22T17:51:42.229Z",
        "created_at": "2020-03-22T17:51:42.231Z"
      },
      "destination": {
        "id": "des_5b3mzbxk83c8qkr",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "My API",
        "alias": null,
        "description": null,
        "url": "https://example.com/webhook",
        "archived_at": null,
        "updated_at": "2020-03-22T17:51:42.228Z",
        "created_at": "2020-03-22T17:51:42.231Z"
      },
      "ruleset": {
        "id": "rls_5b3mzbxk83c0k89",
        "alias": null,
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Default Ruleset",
        "description": null,
        "retry_count": 5,
        "retry_interval": 3600000,
        "retry_strategy": "linear",
        "is_team_default": true,
        "archived_at": null,
        "updated_at": "2020-03-22T17:45:20.742Z",
        "created_at": "2020-03-22T17:45:20.746Z"
      }
    }
  ]
}
```

This endpoint retrieves all webhooks.

### HTTP Request

`GET https://api.hookdeck.io/webhooks`

### Query Parameter

| Parameter | Type      | Description                                 |
| --------- | --------- | ------------------------------------------- |
| archived  | `boolean` | Include the archived ressources in response |

## Retrieve a webhook

> The command returns JSON structured like this

```json
{
    "id": "web_5b3mzbxk83c8qml",
    "label": "Shopify to My API",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "archived_at": null,
    "updated_at": "2020-03-22T17:51:42.286Z",
    "created_at": "2020-03-22T17:51:42.290Z",
    "source": {
        "id": "src_5b3mzbxk83c8qky",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Shopify",
        "alias": null,
        "description": null,
        "archived_at": null,
        "updated_at": "2020-03-22T17:51:42.229Z",
        "created_at": "2020-03-22T17:51:42.231Z"
    },
    "destination": {
        "id": "des_5b3mzbxk83c8qkr",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "My API",
        "alias": null,
        "description": null,
        "url": "https://example.com/webhook",
        "archived_at": null,
        "updated_at": "2020-03-22T17:51:42.228Z",
        "created_at": "2020-03-22T17:51:42.231Z"
    },
    "ruleset": {
        "id": "rls_5b3mzbxk83c0k89",
        "alias": null,
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Default Ruleset",
        "description": null,
        "retry_count": 5,
        "retry_interval": 3600000,
        "retry_strategy": "linear",
        "is_team_default": true,
        "archived_at": null,
        "updated_at": "2020-03-22T17:45:20.742Z",
        "created_at": "2020-03-22T17:45:20.746Z"
    }
```

This endpoint retrieves a specific webhook.

### HTTP Request

`GET https://api.hookdeck.io/webhooks/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Webhook ID  |

## Create a webhook with an undefined destination, source and ruleset

> The command returns JSON structured like this

```json
    //Request
{
	"label": "Github to My API",
	"destination": {
		"label": "My API",
		"url": "http://localhost:9000/attempt_test"
	},
	"source": {
		"label": "Github"
	}
}
    //Response
{
    "id": "web_12n4ffxk8aayze2",
    "label": "Github to My API",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "archived_at": null,
    "updated_at": "2020-03-27T14:50:30.701Z",
    "created_at": "2020-03-27T14:50:30.701Z",
    "destination": {
        "id": "des_12n4ffxk8aayzdb",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "My API",
        "alias": null,
        "description": null,
        "url": "http://localhost:9000/attempt_test",
        "archived_at": null,
        "updated_at": "2020-03-27T14:50:30.689Z",
        "created_at": "2020-03-27T14:50:30.688Z"
    },
    "source": {
        "id": "src_12n4ffxk8aayzdp",
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Github",
        "alias": null,
        "description": null,
        "archived_at": null,
        "updated_at": "2020-03-27T14:50:30.690Z",
        "created_at": "2020-03-27T14:50:30.688Z"
    },
    "ruleset": {
        "id": "rls_5b3mzbxk83c0k89",
        "alias": null,
        "team_id": "tm_5b3mzbxk83c0k7i",
        "label": "Default Ruleset",
        "description": null,
        "retry_count": 5,
        "retry_interval": 3600000,
        "retry_strategy": "linear",
        "is_team_default": true,
        "archived_at": null,
        "updated_at": "2020-03-22T17:45:20.742Z",
        "created_at": "2020-03-22T17:45:20.746Z"
    }
}
```

This endpoint creates a webhook.

### HTTP Request

`POST https://api.hookdeck.io/webhook/`

**Webhook**

| Parameter | Default  | Description                    |
| --------- | -------- | ------------------------------ |
| label     | `string` | Name of the webhook            |
| alias     | `string` | Alternate name for the webhook |

**Source**

| Parameter   | Default | Description                   |
| ----------- | ------- | ----------------------------- |
| label       |         | Name of the source            |
| alias       | `null`  | Alternate name for the source |
| description | `null`  | Description of the source     |

**Destination**

| Parameter   | Default  | Description                        |
| ----------- | -------- | ---------------------------------- |
| label       | `string` | Name of the destination            |
| alias       | `string` | Alternate name for the destination |
| description | `string` | Description of the destination     |
| url         | url      | Endpoint of the destination        |

**Ruleset (optional)**

| Parameter      | Default  | Description                         |
| -------------- | -------- | ----------------------------------- |
| alias          | `string` | Alternate name for the ruleset      |
| label          | `string` | Name of the ruleset                 |
| description    | `string` | Description of the ruleset          |
| retry_count    | integer  | Number of retry attempts            |
| retry_interval | integer  | Time interval between retries in ms |

**Response**

The response returns an ID used in the webhook's unique URL. Use this URL to update the endpoint on your systems.

The format of Hookdeck's URL is  
`https://events.hookdeck.io/e/:id`

Example for Stripe to My API: https://events.hookdeck.io/e/web_5b3mzbxk83dcij0

## Create a webhook with destination ID, source ID and ruleset ID

> The command returns JSON structured like this

```json
    //Request
{
	"label": "Stripe to My API",
	"source_id": "src_5b3mzbxk83dciin",
    "destination_id": "des_5b3mzbxk83dciim",
	"ruleset_id": "rls_5b3mzbxk83c0k89"
}
    //Response
{
     "id": "web_5b3mzbxk83dcij0",
     "label": "Stripe to My API",
     "alias": null,
     "team_id": "tm_5b3mzbxk83c0k7i",
     "archived_at": null,
     "updated_at": "2020-03-22T18:22:38.024Z",
     "created_at": "2020-03-22T18:22:38.028Z",
     "source": {
         "id": "src_5b3mzbxk83dciin",
         "team_id": "tm_5b3mzbxk83c0k7i",
         "label": "Stripe",
         "alias": null,
         "description": null,
         "archived_at": null,
         "updated_at": "2020-03-22T18:22:38.012Z",
         "created_at": "2020-03-22T18:22:38.015Z"
     },
     "destination": {
         "id": "des_5b3mzbxk83dciim",
         "team_id": "tm_5b3mzbxk83c0k7i",
         "label": "My API",
         "alias": null,
         "description": "Our stripe dev environement",
         "url": "https://example.com/webhook",
         "archived_at": null,
         "updated_at": "2020-03-26T17:15:31.079Z",
         "created_at": "2020-03-22T18:22:38.015Z"
     },
     "ruleset": {
         "id": "rls_5b3mzbxk83c0k89",
         "alias": null,
         "team_id": "tm_5b3mzbxk83c0k7i",
         "label": "Default Ruleset",
         "description": null,
         "retry_count": 5,
         "retry_interval": 3600000,
         "retry_strategy": "linear",
         "is_team_default": true,
         "archived_at": null,
         "updated_at": "2020-03-22T17:45:20.742Z",
         "created_at": "2020-03-22T17:45:20.746Z"
    }
}
```

This endpoint creates a webhook.

### HTTP Request

`POST https://api.hookdeck.io/webhook/`

**Webhook**

| Parameter | Type     | Description         |
| --------- | -------- | ------------------- |
| label     | `string` | Name of the webhook |

**Source**

| Parameter | Type     | Description |
| --------- | -------- | ----------- |
| id        | `string` | Source ID   |

**Destination**

| Parameter | Type     | Description    |
| --------- | -------- | -------------- |
| id        | `string` | Destination ID |

**Ruleset (optional)**

| Parameter | Default  | Description |
| --------- | -------- | ----------- |
| id        | `string` | Ruleset ID  |

**Response**

The response returns an ID used in the webhook's unique URL. Use this URL to update the endpoint on your systems.

The format of Hookdeck's URL is  
`https://events.hookdeck.io/e/:id`

Example for Stripe to My API: https://events.hookdeck.io/e/web_5b3mzbxk83dcij0

## Update a webhook

> The command returns JSON structured like this

```json
{
  "id": "web_12n4ffxk8aayze2",
  "label": "Github (test) hook",
  "alias": null,
  "team_id": "tm_5b3mzbxk83c0k7i",
  "archived_at": null,
  "updated_at": "2020-03-27T15:43:03.535Z",
  "created_at": "2020-03-27T14:50:30.701Z",
  "destination": {
    "id": "des_12n4ffxk8aayzdb",
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "My API",
    "alias": null,
    "description": null,
    "url": "http://localhost:9000/attempt_test",
    "archived_at": null,
    "updated_at": "2020-03-27T14:50:30.689Z",
    "created_at": "2020-03-27T14:50:30.688Z"
  },
  "source": {
    "id": "src_12n4ffxk8aayzdp",
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Github",
    "alias": null,
    "description": null,
    "archived_at": null,
    "updated_at": "2020-03-27T14:50:30.690Z",
    "created_at": "2020-03-27T14:50:30.688Z"
  },
  "ruleset": {
    "id": "rls_5b3mzbxk83c0k89",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Default Ruleset",
    "description": null,
    "retry_count": 5,
    "retry_interval": 3600000,
    "retry_strategy": "linear",
    "is_team_default": true,
    "archived_at": null,
    "updated_at": "2020-03-22T17:45:20.742Z",
    "created_at": "2020-03-22T17:45:20.746Z"
  }
}
```

This endpoint updates a webhook.

### HTTP Request

`PUT https://api.hookdeck.io/webhook/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Webhook ID  |

### Body Parameters

| Parameter | Default  | Description                    |
| --------- | -------- | ------------------------------ |
| label     | `string` | Name of the webhook            |
| alias     | `string` | Alternate name for the webhook |

## Archive a webhook

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

This endpoint archives a webhook.

### HTTP Request

`PUT https://api.hookdeck.io/webhook/:id/archive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Webhook ID  |

<aside class="notice">
The parameter `archived_at`is updated
</aside>

## Unarchive a webhook

> The command returns JSON structured like this

```json
{
  "id": "web_12n4ffxk8aayze2",
  "label": "Github (test) hook",
  "alias": null,
  "team_id": "tm_5b3mzbxk83c0k7i",
  "archived_at": null,
  "updated_at": "2020-03-27T15:44:41.022Z",
  "created_at": "2020-03-27T14:50:30.701Z",
  "destination": {
    "id": "des_12n4ffxk8aayzdb",
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "My API",
    "alias": null,
    "description": null,
    "url": "http://localhost:9000/attempt_test",
    "archived_at": null,
    "updated_at": "2020-03-27T14:50:30.689Z",
    "created_at": "2020-03-27T14:50:30.688Z"
  },
  "ruleset": {
    "id": "rls_5b3mzbxk83c0k89",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Default Ruleset",
    "description": null,
    "retry_count": 5,
    "retry_interval": 3600000,
    "retry_strategy": "linear",
    "is_team_default": true,
    "archived_at": null,
    "updated_at": "2020-03-22T17:45:20.742Z",
    "created_at": "2020-03-22T17:45:20.746Z"
  },
  "source": {
    "id": "src_12n4ffxk8aayzdp",
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Github",
    "alias": null,
    "description": null,
    "archived_at": null,
    "updated_at": "2020-03-27T14:50:30.690Z",
    "created_at": "2020-03-27T14:50:30.688Z"
  }
}
```

This endpoint unarchives a webhook.

### HTTP Request

`PUT https://api.hookdeck.io/webhook/:id/unarchive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Webhook ID  |

<aside class="notice">
The parameter `archived_at`becomes null
</aside>
