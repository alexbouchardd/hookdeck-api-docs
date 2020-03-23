---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - curl

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - webhooks
  - errors

search: true
---

# Introduction

Welcome to the Hookdeck API! You can use our Admin API to manage & created your webhooks proxy.

The API currently only supports `application/json` for both input and output. Header is optional.

# Authentication

> Use Basic Authentication to authorize your request. The username is your API Key and the password is blank:

```shell
curl "https://api.hookdeck.io/"
  -H "Content-Type: application/json"
  -u "${YOUR_API_KEY}:"
```

> Make sure to insert your API key.

Hookdeck uses API keys via Basic Auth to allow access to the API. You can retrieve your Hookdeck API key in your [dashboard](https://hookdeck.io/dashboard).

Hoodeck expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic BASE64_API_TOKEN`

<aside class="notice">
You must replace <code>BASE64_API_TOKEN</code> with your personal API key hash.
</aside>

# Paging

> The pagination objection:

```json
{
  "pagination": {
    "order_by": "created_at",
    "order_direction": "desc",
    "limit": 100,
    "after": "web_2urj7h9puxk6obro3x",
    "before": "web_2urj7h9puxk6obuf6i"
  }
}
```

> Example to get the next page:

```shell
curl "https://api.hoockdeck.io/webhooks?after=web_2urj7h9puxk6obro3x"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

> Example to get the previous page:

```shell
curl "https://api.hoockdeck.io/webhooks?before=web_2urj7h9puxk6obuf6i"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

> Example to get the next page without using the default ordering:

```shell
curl "https://api.hoockdeck.io/webhooks?order_by=updated_at&order_direction=asc&after=web_2urj7h9puxk6obro3x"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

Many `GET` ednpoint are paged. We use Cursor (often called Keyset) based pagination for those endpoints.

To work with Keyset paging all the necessary information will be contain in the response body `pagination` object.

| Parameter | Default        | Description                                                       |
| --------- | -------------- | ----------------------------------------------------------------- |
| order_by  | `"created_at"` | The sortable key to use (options varies base on the ressource )   |
| order_by  | `"desc"`       | The direction to sort it (`"asc"` or `"desc"`)                    |
| limit     | `100`          | The making amount of results returned per query (max: `250`)      |
| after     | `undefined`    | The ID to provide in the query to get the next set of results     |
| before    | `undefined`    | The ID to provide in the query to get the previous set of results |

Unless you have specified a `order_by` or `order_direction` yourself, you can omit it from the next or previous set query. You only have to carry them over if you are not using the ressource default
