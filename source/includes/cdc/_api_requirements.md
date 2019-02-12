# API Requirements

## Endpoint

- Responds to an HTTP GET request
- No additional authentication supported beyond the path and query params, e.g. you can set your base URL to something similar to one of:
    - `https://api.example.com/?token=a7c43be`
    - `https://api.example.com/a7c43be/`

## Parameters

- Parameters are scoped to an entity, e.g. `subscriber` or `event`
- You'll specify which fields of these objects you want sent to your endpoint
    - Let us know the _exact_ Custom Field names and Event property names you want us to pass to you via the query string
    - This limitation (not sending all of them) exists because most HTTP servers enforce a URI length limit, and we're passing these fields to you via GET in order for them to be highly cacheable, as to optimize for delivery throughput
- Scoped parameters are then named the same as the custom field
    - e.g. A subscriber custom field of `first_name` would be passed through as `subscriber[first_name]`
    - e.g. An event field of `product_id` would be passed through as `event[product_id]`
- The `event` object is valid only within a Workflow
- Parameters will all be passed via the URL query string (we only support `GET` requests)
- There can be default parameters embedded in your endpoint URL
    - We will append our parameters to yours
    - This is useful for authentication, such as providing `?key=12345`
- Parameters without a value will be sent through as a key with no value
    - e.g. A subscriber with a custom field assigned for country, but not for zip would have a URL query string of `?subscriber[country]=US&subscriber[zip]`
- A parameter value should not be unique per subscriber (e.g. we won't send `email`); this allows for greater cacheability of responses, as to optimize your delivery throughput

## Response

- Responses must have a `Content-Type` header of `application/json`
- A response with a `2xx` status will be considered successful
- A successful response must contain a body that is a parseable JSON _document_ (i.e. the top level must be either an object or an array)
- A `3xx` response will be followed as redirects per the HTTP specification
- Response codes in the `4xx` and `5xx` ranges will be considered an error
- No other response codes are supported
- The returned document cannot exceed 350 KB in size

When a `2xx` response is received, Drip will use whatever data is given, and will assume `null` values for any data not given. For example, response of `{}` would still be accessible in Liquid and would respond to any attribute with `nil`.

## General

- We will retry failed responses (`4xx` or `5xx`) for a limited amount of time
- If retries continue to fail, we will give up sending the individual email
- In order to optimize your sending throughput, we will time out any response or series of redirects after 3 seconds
