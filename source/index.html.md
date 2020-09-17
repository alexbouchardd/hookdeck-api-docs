---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - curl

toc_footers:
  - <a href='https://hookdeck.io/signin'>Sign Up for a Developer Key</a>
  - <a href='https://https://spectrum.chat/hookdeck?tab=chat'>Ask a question</a>

includes:
  - sources
  - destinations
  - rulesets
  - webhooks
  - events
  - attempts
  - paging
  - bestpractices
  - errors
  - moreinformation
  - gethelp

search: true

code_clipboard: true
---

# Get Started

Welcome to the Hookdeck Admin API! Our API allows you set up your webhooks, view your events and perform various actions such as retries. Explore our data, browse descriptions of the available attributes and see examples of working requests and responses.

To learn move about Hookdeck view our official website at [https://hookdeck.io](https://hookdeck.io)

## Create your account

It won't come as a surprise the first step to create your account at [https://hookdeck.io/signin](https://hookdeck.io/signin). You can create an account using your Github or Google account. Along with any new account a new 'Deck' (Project) will be created. A Deck can container as many webhooks as you want.

## Authentication

> Use Basic Authentication to authorize your request. The username is your API Key and the password is blank:

```shell
curl "https://api.hookdeck.io/" \
  -H "Content-Type: application/json" \
  -u "${YOUR_API_KEY}:"
```

> Make sure to insert your API key.

Hookdeck uses API keys via Basic Auth to allow access to the API. You can retrieve your Hookdeck API key in your [dashboard](https://hookdeck.io/dashboard/api).

Hookdeck expects your API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic BASE64_API_TOKEN`

<aside class="notice">
You must replace <code>BASE64_API_TOKEN</code> with your personal API key hash.
</aside>

## Webhook configuration

A webhook is essentially a Webhook 'Proxy' that is composed of 3 things, a source, a destination and a ruleset.

### Sources

A source is a representation of the service your are planning on receiving your webhooks from. That could be Shopify, Stripe, Intercom, Mailchimp or any other service. Setting a source on a webhook is mandatory to allow Hookdeck to be able to identify the webhook provider.

<aside class="notice">
As of right now, no signature verification is performed, however, we will eventually add the ability to verify the webhook signature and configuration in your sources might be required.
</aside>

### Destinations

> The appended headers are:

```
'X-Hookdeck-EventID':        Hookdeck event id,
'X-Hookdeck-Signature':      Hookdeck custom event signature,
'X-Hookdeck-Attempt-Count':  Event attempt number,
'X-Hookdeck-Event-URL':      Url to the hookdeck dashboard for that event
```

A destination is a representation of your own API where the webhooks will be delivered. Each destination requires a HTTP URL that will receive a `POST` request with a `JSON` body payload. Each webhook event will also contain the original HTTP Headers along with additional headers from Hookdeck. The body data is always left untouched.

### Rulesets

A ruleset is a reusable set of configuration to set the retry logic for any event associated with a webhook. The retry logic has 2 params:

- Retry count `retries_count` is the maximum number of automatic retry that will be attempted. As soon as an event attempt receives a `2xx` status, no other attempts will be made
- Retries interval `retries_interval` is the delays in milliseconds between retry. Retries are always rounded to the nearest minute (therefore the minimum delay is 60000ms).

<aside class="notice">
Each new account comes with a 'Default Ruleset' that is automatically added to any webhook without a manually associated ruleset. The 'Default Ruleset' has a `retries_count` of `5` and a `retries_interval` of `3600000` (one hour). Therefore, any webhook will be default ruleset will be retried up to 5 times over a 5 hour period.
</aside>

## Create your first webhook

> Header

```shell
curl "POST https://api.hookdeck.io/webhooks" \
  -H "Authorization: Basic {{ BASE64_API_TOKEN }}" \
  -H "Content-Type: application/json"
```

> Body

```json
{
  "label": "Shopify to My API",
  "source": {
    "label": "Shopify"
  },
  "destination": {
    "label": "My API",
    "url": "https://example.com/webhook"
  }
}
```

> Example returned body

```json
{
  "id": "web_xxxxxxxxxxxxxxx",
  "label": "Shopify to My API",
  "alias": null,
  "team_id": "tm_xxxxxxxxxxxxxxx",
  "archived_at": null,
  "updated_at": "2020-03-22T01:07:38.162Z",
  "created_at": "2020-03-22T01:07:38.161Z",
  "destination": {
    "id": "des_xxxxxxxxxxxxxxx",
    "team_id": "tm_xxxxxxxxxxxxxxx",
    "label": "My API",
    "alias": null,
    "description": null,
    "url": "https://example.com/webhook",
    "archived_at": null,
    "updated_at": "2020-03-22T01:07:38.154Z",
    "created_at": "2020-03-22T01:07:38.149Z"
  },
  "ruleset": {
    "id": "rls_xxxxxxxxxxxxxxx",
    "alias": null,
    "team_id": "tm_xxxxxxxxxxxxxxx",
    "label": "Default Ruleset",
    "description": null,
    "retry_count": 5,
    "retry_interval": 3600000,
    "retry_strategy": "linear",
    "is_team_default": true,
    "archived_at": null,
    "updated_at": "2020-03-22T01:00:37.647Z",
    "created_at": "2020-03-22T01:00:37.647Z"
  },
  "source": {
    "id": "src_xxxxxxxxxxxxxxx",
    "team_id": "tm_xxxxxxxxxxxxxxx",
    "label": "Shopify",
    "alias": null,
    "description": null,
    "archived_at": null,
    "updated_at": "2020-03-22T01:07:38.155Z",
    "created_at": "2020-03-22T01:07:38.150Z"
  }
}
```

> Example reusing a ressource

```json
{
  "label": "Shopify to My API",
  "destination_id": "des_xxxxxxxxxxxxxxx",
  "source_id": "src_xxxxxxxxxxxxxxx",
  "ruleset_id": "rls_xxxxxxxxxxxxxxx"
}
```

When you create your first webhook, you can pass a `destination` and `source` definition. Along with the request, all the required ressources will be created. When a webhook is created without a `ruleset`, the default ruleset is applied.

### Mandatory parameters

**Webhook**

| Parameter | Type  | Description         |
| --------- | ------ | ------------------- |
| label     | `string` | Name of the webhook |

**Source**

| Parameter | Type  | Description        |
| --------- | ------ | ------------------ |
| label     | `string` | Name of the source |

**Destination**

| Parameter | Type  | Description                 |
| --------- | ------ | --------------------------- |
| label     | `string` | Name of the destination     |
| url       | url    | Endpoint of the destination |

The body returns an ID for the source, destination and ruleset generated for the webhook. They can be reused by passing the `destination_id`, `source_id` or `ruleset_id` instead of an object.

<aside class="notice">
The API currently only supports `application/json` for both input and output. Header is optional.
</aside>

## Monitoring

All events that are handled by Hookdeck can be viewed, inspected, filtered, sorted, manually retried and cancelled in your dashboard or with the API.
