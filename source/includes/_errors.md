# Errors

> Example response from an error

```json
{
  "handled": true,
  "status": 422,
  "message": "Webhook does not exist or is archived",
  "data": {
    "id": "web_xxxxxxxxxxx"
  }
}
```

Hookdeck uses standard HTTP response codes to indicate success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided information (e.g., a required parameter was missing), and codes in the 5xx range indicate an error.

## Response

With any HTTP error the response body will contain a few properties.

| Parameter | Type      | Description                                                                            |
| --------- | --------- | -------------------------------------------------------------------------------------- |
| handle    | `boolean` | Error was handled by the API and did not resolve in a uncaugh exception.               |
| status    | `integer` | HTTP Status of the error                                                               |
| message   | `string`  | Message associated to the error, could be more or less specific depending on the error |
| data      | `object`  | Data related to the error, useful for diagnostics                                      |

## Error Codes

| Status Code | Explanation                                                                               |
| ----------- | ----------------------------------------------------------------------------------------- |
| 200         | Good Request -- Your request is valid.                                                    |
| 400         | Bad Request -- Your request is invalid and could not be understood.                       |
| 401         | Unauthorized -- Your API key is wrong.                                                    |
| 403         | Forbidden -- The ressouce requested access is restricted.                                 |
| 404         | Not Found -- The ressource could not be found.                                            |
| 422         | Unprocessable Entry -- Your request was understood but contains invalid input.            |
| 500         | Internal Server Error -- We had a problem with our server. Try again later.               |
| 503         | Service Unavailable -- We're temporarily offline for maintenance. Please try again later. |
