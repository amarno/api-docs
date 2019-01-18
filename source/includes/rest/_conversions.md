# Conversions

> Conversions are represented as follows:

```json
{
  "id": "99999",
  "status": "active",
  "name": "Trial Signup",
  "url": "/receipt",
  "default_value": 2000,
  "counting_method": "one_per_visitor",
  "created_at": "2013-06-21T10:31:58Z",
  "href": "https://api.getdrip.com/v2/9999999/goals/99999",
  "links": {
    "account": "9999999"
  }
}
```

> All responses containing conversion data also include the following top-level link data:

```json
{
  "links": {
    "goals.account": "https://api.getdrip.com/v2/accounts/{goals.account}"
  }
}
```

**Properties**

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>A read-only Drip generated unique id used to identify each conversion record.</td>
    </tr>
    <tr>
      <td><code>status</code></td>
      <td>Returns whether the conversion is enabled or disabled.</td>
    </tr>
    <tr>
      <td><code>name</code></td>
      <td>The private name given to the conversion.</td>
    </tr>
    <tr>
      <td><code>url</code></td>
      <td>A URL used for detecting and recording conversions.</td>
    </tr>
    <tr>
      <td><code>default_value</code></td>
      <td>A default value assigned to a tracked conversion.
      Conversion values must be less than 2,147,483,647.
      </td>
    </tr>
    <tr>
      <td><code>counting_method</code></td>
      <td>Set either as <code>one_per_visitor</code> or <code>all</code> and determines whether a maximum of one conversion is counted per person or all.</td>
    </tr>
    <tr>
      <td><code>created_at</code></td>
      <td>A timestamp representing when the conversion was first created.</td>
    </tr>
    <tr>
      <td><code>href</code></td>
      <td>The url designated for retrieving the conversion record via the REST API.</td>
    </tr>
    <tr>
      <td><code>links</code></td>
      <td>An object containing the REST API URL for the account.</td>
    </tr>
  </tbody>
</table>

See the Events API for recording conversion events.

## List all conversions

> To list all conversions in an account:

```shell
curl "https://api.getdrip.com/v2/YOUR_ACCOUNT_ID/goals" \
  -H 'User-Agent: Your App Name (www.yourapp.com)' \
  -u YOUR_API_KEY:
```

```ruby
require 'drip'

client = Drip::Client.new do |c|
  c.api_key = "YOUR API KEY"
  c.account_id = "YOUR_ACCOUNT_ID"
end

response = client.conversions

if response.success?
  puts response.body["goals"]
end
```

```javascript
// npm install drip-nodejs --save

const client = require('drip-nodejs')({ token: YOUR_API_KEY, accountId: YOUR_ACCOUNT_ID });
const options = { status: "active" };

client.listConversions(options)
  .then((response) => {
    // Handle `response.body`
  })
  .catch((error) => {
    // Handle errors
  });
```

> The response looks like this:

```json
# The goals property is an array of conversion goal objects.
{
  "links": { ... },
  "goals": [ ... ]
}
```

### HTTP Endpoint

`GET /v2/:account_id/goals`

### Arguments

<table>
  <thead>
    <tr>
      <th>Key</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>status</code></td>
      <td>Optional. The status to filter by: <code>active</code>, <code>disabled</code>, or <code>all</code>. Defaults to <code>all</code>.</td>
    </tr>
    <tr>
      <td><code>sort</code></td>
      <td>Optional. Sort results by one of these fields: <code>created_at</code> or <code>name</code>. Defaults to <code>created_at</code>.</td>
    </tr>
    <tr>
      <td><code>direction</code></td>
      <td>Optional. Filter sort direction with: <code>asc</code> or <code>desc</code>. Defaults to <code>asc</code>.</td>
    </tr>
  </tbody>
</table>

## Fetch a conversion

> To fetch a conversion:

```shell
curl "https://api.getdrip.com/v2/YOUR_ACCOUNT_ID/goals/CONVERSION_ID" \
  -H 'User-Agent: Your App Name (www.yourapp.com)' \
  -u YOUR_API_KEY:
```

```ruby
require 'drip'

client = Drip::Client.new do |c|
  c.api_key = "YOUR API KEY"
  c.account_id = "YOUR_ACCOUNT_ID"
end

conversion_id = 9999999
response = client.conversion(conversion_id)

if response.success?
  puts response.body["goals"]
end
```

```javascript
// npm install drip-nodejs --save

const client = require('drip-nodejs')({ token: YOUR_API_KEY, accountId: YOUR_ACCOUNT_ID });
const conversionId = 8889999;

client.fetchConversion(conversionId)
  .then((response) => {
    // Handle `response.body`
  })
  .catch((error) => {
    // Handle errors
  });
```

> The response looks like this:

```json
# The goals property is an array of one conversion goal object.
{
  "links": { ... },
  "goals": [{ ... }]
}
```

### HTTP Endpoint

`GET /v2/:account_id/goals/:conversion_id`

### Arguments

None.
