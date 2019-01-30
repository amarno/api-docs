# Users

> Users are represented as follows:

```json
{
  "email": "john@acme.com",
  "name": "John Doe",
  "time_zone": "America/Los_Angeles"
}
```

## Fetch the authenticated user

> To fetch the current user:

```shell
curl "https://api.getdrip.com/v2/user" \
  -H 'User-Agent: Your App Name (www.yourapp.com)' \
  -u YOUR_API_KEY:
```

```javascript
// npm install drip-nodejs --save

const client = require('drip-nodejs')({ token: YOUR_API_KEY, accountId: YOUR_ACCOUNT_ID });

client.fetchUser()
  .then((response) => {
    // Handle `response.body`
  })
  .catch((error) => {
    // Handle errors
  });
```

> The response looks like this:

```json
{
  "users":[{
    "email": "john@acme.com",
    "name": "John Doe",
    "time_zone": "America/Los_Angeles"
  }]
}
```

### HTTP Endpoint

`GET /v2/user`

### Arguments

None.
