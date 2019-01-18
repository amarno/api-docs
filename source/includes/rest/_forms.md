# Forms

> Forms are represented as follows:

```json
{
  "id": "77777",
  "href": "https://api.getdrip.com/v2/9999999/forms/77777",
  "headline": "Long Tail SEO Course",
  "description": "Get our FREE email course",
  "button_text": "Sign Up!",
  "confirmation_heading": "Thank you for subscribing",
  "confirmation_text": "Please click the link in your email",
  "send_ga_event": true,
  "seconds_before_popup": 5,
  "days_between_popup": 5,
  "days_between_popup_after_close": 10,
  "orientation": "bottom_right_tab",
  "opacity": 0.8,
  "show_labels": false,
  "primary_color": "#333333",
  "secondary_color": "#d8ab93",
  "is_widget_enabled": true,
  "whitelist": [ "/landing", "/public" ],
  "blacklist": [],
  "is_whitelist_enabled": true,
  "is_blacklist_enabled": false,
  "hide_on_mobile": false,
  "is_embeddable": true,
  "created_at": "2013-06-21T10:31:58Z",
  "links": {
    "account": "9999999"
  }
}
```

> All responses containing form data also include the following top-level link data:

```json
{
  "links": {
    "forms.account": "https://api.getdrip.com/v2/accounts/{forms.account}"
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
      <td>A read-only Drip generated unique id used to identify each form record.</td>
    </tr>
    <tr>
      <td><code>href</code></td>
      <td>The url designated for retrieving the form record via the REST API.</td>
    </tr>
    <tr>
      <td><code>headline</code></td>
      <td>The visible headline on the form widget or embedded form.</td>
    </tr>
    <tr>
      <td><code>description</code></td>
      <td>A description shown in the body of the form widget or in the embedded form.</td>
    </tr>
    <tr>
      <td><code>button_text</code></td>
      <td>The text shown on the submission button for the form.</td>
    </tr>
    <tr>
      <td><code>confirmation_heading</code></td>
      <td>A heading shown after a subscriber submits the form.</td>
    </tr>
    <tr>
      <td><code>confirmation_text</code></td>
      <td>The text shown after a subscriber submits the form.</td>
    </tr>
    <tr>
      <td><code>send_ga_event</code></td>
      <td>Returns true if an event is sent to Google Analytics upon submission.</td>
    </tr>
    <tr>
      <td><code>seconds_before_popup</code></td>
      <td>A delay in seconds before the form widget is displayed.</td>
    </tr>
    <tr>
      <td><code>days_between_popup</code></td>
      <td>A delay in days between each appearance of the form widget.</td>
    </tr>
    <tr>
      <td><code>days_between_popup_after_close</code></td>
      <td>A delay in days between each appearance of the form widget after a visitor closes the form.</td>
    </tr>
    <tr>
      <td><code>orientation</code></td>
      <td>The position on the page where the form widget is displayed. Possible values are <code>bottom_left_tab</code>, <code>bottom_right_tab</code>, <code>side_left_tab</code>, <code>side_right_tab</code>, <code>embedded</code> or <code>lightbox</code>.</td>
    </tr>
    <tr>
      <td><code>opacity</code></td>
      <td>The opacity set for form field labels.</td>
    </tr>
    <tr>
      <td><code>show_labels</code></td>
      <td>Returns true if form field labels are shown above text boxes.</td>
    </tr>
    <tr>
      <td><code>primary_color</code></td>
      <td>The tab color for the form.</td>
    </tr>
    <tr>
      <td><code>secondary_color</code></td>
      <td>The headline color for the form.</td>
    </tr>
    <tr>
      <td><code>is_widget_enabled</code></td>
      <td>Returns true if the form widget is enabled and shown.</td>
    </tr>
    <tr>
      <td><code>whitelist</code></td>
      <td>An array of URL paths where the form is shown.</td>
    </tr>
    <tr>
      <td><code>blacklist</code></td>
      <td>An array of URL paths where the form is hidden.</td>
    </tr>
    <tr>
      <td><code>is_whitelist_enabled</code></td>
      <td>Returns true if whitelisted URLs are set.</td>
    </tr>
    <tr>
      <td><code>is_blacklist_enabled</code></td>
      <td>Returns true if blacklisted URLs are set.</td>
    </tr>
    <tr>
      <td><code>hide_on_mobile</code></td>
      <td>Returns true if the form widget is disabled for mobile devices.</td>
    </tr>
    <tr>
      <td><code>is_embeddable</code></td>
      <td>Deprecated</td>
    </tr>
    <tr>
      <td><code>created_at</code></td>
      <td>A timestamp representing when the form was first created.</td>
    </tr>
    <tr>
      <td><code>links</code></td>
      <td>An object containing the REST API URL for the account.</td>
    </tr>
  </tbody>
</table>

## List all forms

> To list all forms in an account:

```shell
curl "https://api.getdrip.com/v2/YOUR_ACCOUNT_ID/forms" \
  -H 'User-Agent: Your App Name (www.yourapp.com)' \
  -u YOUR_API_KEY:
```

```ruby
require 'drip'

client = Drip::Client.new do |c|
  c.api_key = "YOUR API KEY"
  c.account_id = "YOUR_ACCOUNT_ID"
end

response = client.forms

if response.success?
  puts response.body["forms"]
end
```

```javascript
// npm install drip-nodejs --save

const client = require('drip-nodejs')({ token: YOUR_API_KEY, accountId: YOUR_ACCOUNT_ID });

client.listForms()
  .then((response) => {
    // Handle `response.body`
  })
  .catch((error) => {
    // Handle errors
  });
```

> The response looks like this:

```json
# The forms property is an array of form objects.
{
  "links": { ... },
  "forms": [ ... ]
}
```

### HTTP Endpoint

`GET /v2/:account_id/forms`

### Arguments

None.

## Fetch a form

> To fetch a specific form:

```shell
curl "https://api.getdrip.com/v2/YOUR_ACCOUNT_ID/forms/FORM_ID" \
  -H 'User-Agent: Your App Name (www.yourapp.com)' \
  -u YOUR_API_KEY:
```

```ruby
require 'drip'

client = Drip::Client.new do |c|
  c.api_key = "YOUR API KEY"
  c.account_id = "YOUR_ACCOUNT_ID"
end

form_id = 9999999
response = client.form(form_id)

if response.success?
  puts response.body["forms"]
end
```

```javascript
// npm install drip-nodejs --save

const client = require('drip-nodejs')({ token: YOUR_API_KEY, accountId: YOUR_ACCOUNT_ID });
const formId = 9998888;

client.fetchForm(formId)
  .then((response) => {
    // Handle `response.body`
  })
  .catch((error) => {
    // Handle errors
  });
```

> The response looks like this:

```json
# The forms property is an array of one form object.
{
  "links": { ... },
  "forms": [{ ... }]
}
```

### HTTP Endpoint

`GET /v2/:account_id/forms/:form_id`

### Arguments

None.
