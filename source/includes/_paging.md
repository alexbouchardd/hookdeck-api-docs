# Paging

> The pagination objection:

```json
{
  "pagination": {
    "order_by": "created_at",
    "dir": "desc",
    "limit": 100,
    "next": "web_2urj7h9puxk6obro3x",
    "prev": "web_2urj7h9puxk6obuf6i"
  }
}
```

> Example to get the next page:

```shell
curl "https://api.hoockdeck.io/webhooks?next=web_2urj7h9puxk6obro3x"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

> Example to get the previous page:

```shell
curl "https://api.hoockdeck.io/webhooks?previous=web_2urj7h9puxk6obuf6i"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

> Example to get the next page without using the default ordering:

```shell
curl "https://api.hoockdeck.io/webhooks?order_by=updated_at&dir=asc&next=web_2urj7h9puxk6obro3x"
  -H "Authorization: Basic BASE64_API_TOKEN"
```

Many `GET` ednpoint are paged. We use Cursor (often called Keyset) based pagination for those endpoints.

To work with Keyset paging all the necessary information will be contain in the response body `pagination` object.

| Parameter | Default        | Description                                                       |
| --------- | -------------- | ----------------------------------------------------------------- |
| order_by  | `"created_at"` | The sortable key to use (options varies base on the resource )    |
| dir       | `"desc"`       | The direction to sort it (`"asc"` or `"desc"`)                    |
| limit     | `100`          | The making amount of results returned per query (max: `250`)      |
<<<<<<< Updated upstream
| next      | `undefined`    | The ID to provide in the query to get the next set of results     |
| prev      | `undefined`    | The ID to provide in the query to get the previous set of results |

Unless you have specified a `order_by` or `dir` yourself, you can omit it from the next or previous set query. You only have to carry them over if you are not using the resource default

<aside class="notice">
If an event is pending, the keyset will return a truthy value (null) which will cause the pagination to omit null values in the response.   
</aside>
=======
| next     | `undefined`    | The cursor to provide in the query to get the next set of results     |
| previous    | `undefined`    | The cursor to provide in the query to get the previous set of results |

Unless you have specified a `order_by` or `dir` yourself, you can omit it from the next or previous set query. You only have to carry them over if you are not using the resource default.
>>>>>>> Stashed changes
