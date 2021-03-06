# Rulesets

> Endpoints

```
GET      /rulesets
GET      /rulesets/:id
POST     /rulesets
PUT      /rulesets/:id
PUT      /rulesets/:id/archive
PUT      /rulesets/:id/unarchive
```

Ruleset objects allows you to set an automaic retry logic and alert strategy for a specific combination of source and destination.

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
  "created_at": "2020-03-22T17:45:20.746Z",
  "alert_interval": 3600000,
  "alert_strategy": "last_attempt"
}
```

When a webhook is created without a ruleset, the default ruleset is applied. Optionally you can create a new ruleset.

| Parameter       | Type      | Default             | Description                             |
| --------------- | --------- | ------------------- | --------------------------------------- |
| id              | `string`  |                     | Ruleset ID                              |
| alias           | `string`  | `null`              | Alternate name for the ruleset          |
| team_id         | `string`  |                     | Deck ID                                 |
| label           | `string`  | `"Default Ruleset"` | Name of the ruleset                     |
| description     | `string`  | `null`              | Description of the ruleset              |
| retry_count     | `integer` | `5`                 | Number of retry attempts                |
| retry_interval  | `integer` | `3600000`           | Time interval between retries in ms     |
| retry_strategy  | `string`  | `"linear"`          | Apply linear between interval retries   |
| is_team_default | `boolean` | `true`              | Default ruleset of Deck                 |
| archived_at     | `date`    | `null`              | Date the ruleset was archived           |
| updated_at      | `date`    |                     | Last `ISO Date` the ruleset was updated |
| created_at      | `date`    |                     | Date the ruleset was created            |
| alert interval  | `integer` | `3600000`           | Time interval between alerts in ms      |
| alert strategy  | `string`  | `last_attempt`      | Alert strategy for the ruleset          |

## Retrieve all rulesets

> The command returns JSON structured like this

```json
{
  "pagination": {
    "order_by": "created_at",
    "dir": "desc",
    "limit": 100,
    "next": "rls_5b3mzbxk83c0k89",
    "prev": "rls_1b69dxk891v0g0"
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
      "created_at": "2020-03-26T17:47:42.725Z",
      "alert_interval": 3600000,
      "alert_strategy": "each_attempt"
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
      "created_at": "2020-03-22T17:45:20.746Z",
      "alert_interval": 3600000,
      "alert_strategy": "last_attempt"
    }
  ]
}
```

This endpoint retrieves all rulesets.

### HTTP Request

`GET https://api.hookdeck.io/rulesets`

### Query Parameter

| Parameter | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| archived  | `boolean` | Include the archived resources in response |

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
  "created_at": "2020-03-26T17:47:42.725Z",
  "alert_interval": 3600000,
  "alert_strategy": "each_attempt"
}
```

This endpoint retrieves a specific ruleset.

### HTTP Request

`GET https://api.hookdeck.io/rulesets/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Ruleset ID  |

## Create a ruleset

> The command returns JSON structured like this

```json
{
  "id": "rls_1b69dxk8922ozz",
  "alias": null,
  "label": "Ruleset 2",
  "description": "Wait 2 minutes",
  "retry_count": 5,
  "retry_interval": 7200000,
  "team_id": "tm_5b3mzbxk83c0k7i",
  "created_at": "2020-03-26T17:53:41.135Z",
  "alert_interval": 3600000,
  "alert_strategy": "last_attempt"
}
```

This endpoint creates a ruleset.

### HTTP Request

`POST https://api.hookdeck.io/ruleset/`

| Parameter      | Type      | Description                                                         |
| -------------- | --------- | ------------------------------------------------------------------- |
| alias          | `string`  | Alternate name for the ruleset                                      |
| label          | `string`  | Name of the ruleset                                                 |
| description    | `string`  | Description of the ruleset                                          |
| retry_count    | `integer` | Number of retry attempts                                            |
| retry_interval | `integer` | Time interval between retries in ms                                 |
| alert interval | `integer` | Time interval between alerts in ms                                  |
| alert strategy | `string`  | Alert strategy for the ruleset (null, each_attempt or last_attempt) |

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
  "created_at": "2020-03-26T17:53:41.135Z",
  "alert_interval": 3600000,
  "alert_strategy": "last_attempt"
}
```

This endpoint updates a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Ruleset ID  |

### Body Parameters

| Parameter      | Type      | Description                                                         |
| -------------- | --------- | ------------------------------------------------------------------- |
| alias          | `string`  | Alternate name for the ruleset                                      |
| label          | `string`  | Name of the ruleset                                                 |
| description    | `string`  | Description of the ruleset                                          |
| retry_count    | `integer` | Number of retry attempts                                            |
| retry_interval | `integer` | Time interval between retries in ms                                 |
| alert interval | `integer` | Time interval between alerts in ms                                  |
| alert strategy | `string`  | Alert strategy for the ruleset (null, each_attempt or last_attempt) |

<aside class="notice">
If alert_strategy is null, alerts are disabled.
If alert_interval is null then you might receive a lot of alerts...
</aside>

## Archive a ruleset

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
  "archived_at": "2020-03-27T20:21:35.975Z",
  "updated_at": "2020-03-27T20:21:35.975Z",
  "created_at": "2020-03-26T17:53:41.135Z",
  "alert_interval": 3600000,
  "alert_strategy": "last_attempt"
}
```

This endpoint archives a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id/archive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Ruleset ID  |

<aside class="notice">
The parameter `archived_at`is updated
</aside>

## Unarchive a ruleset

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
  "updated_at": "2020-03-27T20:21:36.975Z",
  "created_at": "2020-03-26T17:53:41.135Z",
  "alert_interval": 3600000,
  "alert_strategy": "last_attempt"
}
```

This endpoint unarchives a ruleset.

### HTTP Request

`PUT https://api.hookdeck.io/ruleset/:id/unarchive`

### URL Parameter

| Parameter | Description |
| --------- | ----------- |
| id        | Ruleset ID  |

<aside class="notice">
The parameter `archived_at`becomes null
</aside>
