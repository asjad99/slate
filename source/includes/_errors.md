# Errors

<aside class="notice">The Semantic Search API uses the following error codes:
.</aside>



Error Code | Meaning
---------- | -------
400 | Bad Request -- Check your request syntax.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The requested functionality is hidden for administrators only.
404 | Not Found -- The specified document could not be found.
429 | Too Many Requests -- You're sending too many requests at once! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
