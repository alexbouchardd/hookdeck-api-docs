# Errors

Hookdeck uses standard HTTP response codes to indicate success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that resulted from the provided information (e.g., a required parameter was missing), and codes in the 5xx range indicate an error.

Status Code | Explanation
---------- | -------
200 | Good Request -- Your request is valid.
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The webhook requested is hidden for administrators only.
404 | Not Found -- The webhook  could not be found.
405 | Method Not Allowed -- You tried to access a webhook with an invalid method.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
