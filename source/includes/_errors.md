# Errors

The Channel Signal API uses the following error codes:

Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your API key is incorrect.
403 | Forbidden -- You are not allowed to perform this action.
404 | Not Found -- The specified resource could not be found.
422 | Unprocessable Entity -- The request failed validation. The response lists the errors by field, e.g. `{"email": ["has already been taken"]}`.
429 | Too Many Requests -- You're requesting too many resources.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
