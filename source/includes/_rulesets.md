#  Rulesets

> Endpoints

```
GET      /rulesets             
GET      /rulesets/:id                   
POST     /rulesets                
PUT      /rulesets/:id                   
PUT      /rulesets/:id/archive                   
PUT      /rulesets/:id/unarchive                   
```

Ruleset objects allows you to set an automaic retry logic for a specific combination of source and destination.

## Ruleset object

```json 
{
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

When a webhook is created without a ruleset, the default ruleset is applied. Optionally you can create a new ruleset.


| Parameter      | Class     | Default    |Description                                 |
| -------------- | --------- | -----------|------------------------------------------- |
|  id            | string    |            | Ruleset ID                   |
|  alias         | string    | null       | Alternate name for the ruleset             ||  team_id       | string    |            | Deck ID                    |
|  label         | string    | Default Ruleset| Name of the ruleset                |
|  description   | string    | null       | Description of the ruleset          |
|  retry_count   | integer   | 5          | Number of retry attempts         |
|  retry_interval| integer   | 3600000    | Time interval between retries in ms    |
|  retry_strategy| string    | 'linear'   | Apply linear between interval retries   |
|  is_team_default | boolean | true       | Default ruleset of Deck          |
|  archived_at   | date      | null       | Date the ruleset was archived         |
|  updated_at    | date      |            | Last date the ruleset was updated          |
|  created_at    | date      |            |Date the ruleset was created         |

## Retrieve all rulesets

> The command returns JSON structured like this

```json 
  {
{
    "pagination": {
        "order_by": "created_at",
        "order_direction": "desc",
        "limit": 100,
        "after": "rls_5b3mzbxk83c0k89",
        "before": "rls_1b69dxk891v0g0"
    },
    "total_count": 2,
    "count": 2,
    "models": [
        {
            "id": "rls_1b69dxk891v0g0",
            "alias": null,
            "team_id": "tm_5b3mzbxk83c0k7i",
            "label": "Ruleset 1",
            "description": null,
            "retry_count": 10,
            "retry_interval": 3600000,
            "retry_strategy": "linear",
            "is_team_default": false,
            "archived_at": null,
            "updated_at": "2020-03-26T17:50:45.710Z",
            "created_at": "2020-03-26T17:47:42.725Z"
        },
        {
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
    ]
}
```

This endpoint retrieves all rulesets.

### HTTP Request

`GET https://api.hookdeck.io/rulesets`

## Retrieve a ruleset

> The command returns JSON structured like this

```json 
{
    "id": "rls_1b69dxk891v0g0",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Ruleset 1",
    "description": null,
    "retry_count": 10,
    "retry_interval": 3600000,
    "retry_strategy": "linear",
    "is_team_default": false,
    "archived_at": null,
    "updated_at": "2020-03-26T17:50:45.710Z",
    "created_at": "2020-03-26T17:47:42.725Z"
}
```

This endpoint retrieves a specific ruleset.

### HTTP Request

`GET https://api.hookdeck.io/rulesets/:id`

### URL Parameter

| Parameter      | Description                                  |
| -------------- | -------------------------------------------- |
|  ID            | Ruleset ID                   |

## Create a ruleset

> The command returns JSON structured like this

```json 
{
    "id": "rls_1b69dxk8922ozz",
    "alias": null ,
    "label": "Ruleset 2",
    "description": "Wait 2 minutes",
    "retry_count": 5,
    "retry_interval": 7200000,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "created_at": "2020-03-26T17:53:41.135Z"
}
```

This endpoint creates a ruleset.

### HTTP Request

`POST https://api.hookdeck.io/ruleset/`

| Parameter      | Class     | Description                                  |
| -------------- | --------- | -------------------------------------------- |
|  alias         | string    | Alternate name for the ruleset          |   
|  label         | string    |  Name of the ruleset                |
|  description   | string    | Description of the ruleset          |
|  retry_count   | integer   |  Number of retry attempts         |
|  retry_interval| integer   | Time interval between retries in ms    |


## Update a ruleset

> The command returns JSON structured like this

```json 
{
    "id": "rls_1b69dxk8922ozz",
    "alias": "Ruleset number 2",
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Ruleset 2",
    "description": "Wait 2 minutes",
    "retry_count": 5,
    "retry_interval": 7200000,
    "retry_strategy": "linear",
    "is_team_default": false,
    "archived_at": null,
    "updated_at": "2020-03-26T20:21:35.975Z",
    "created_at": "2020-03-26T17:53:41.135Z"
}
```

This endpoint updates a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id`

### URL Parameter

| Parameter      | Description                                  |
| -------------- | -------------------------------------------- |
|  ID            | Ruleset ID                   |

### Body Parameters

| Parameter      | Class     | Description                                  |
| -------------- | --------- | -------------------------------------------- |
|  alias         | string    | Alternate name for the ruleset          |   
|  label         | string    |  Name of the ruleset                |
|  description   | string    | Description of the ruleset          |
|  retry_count   | integer   |  Number of retry attempts         |
|  retry_interval| integer   | Time interval between retries in ms    |

## Archive a ruleset TO BE UPDATED

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

This endpoint archives a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id/archive`

### URL Parameter

| Parameter      | Description                                  |
| -------------- | -------------------------------------------- |
|  ID            | Ruleset ID                   |


<aside class="notice">
The parameter "archived_at" is updated
</aside>

## Unarchive a ruleset

> The command returns JSON structured like this

```json 
{
    "id": "rls_12n4ffxk897h4ld",
    "alias": null,
    "team_id": "tm_5b3mzbxk83c0k7i",
    "label": "Ruleset 2",
    "description": "Wait 2 minutes",
    "retry_count": 5,
    "retry_interval": 7200000,
    "retry_strategy": "linear",
    "is_team_default": false,
    "archived_at": null,
    "updated_at": "2020-03-26T20:29:58.912Z",
    "created_at": "2020-03-26T20:24:52.609Z"
}
```

This endpoint unarchives a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id/unarchive`

### URL Parameter

| Parameter      | Description                                  |
| -------------- | -------------------------------------------- |
|  ID            | Ruleset ID                   |

<aside class="notice">
The parameter "archived_at" becomes null
</aside>
