# Preview/Test Mode

> Example request from Drip to your endpoint during Preview/Test

```bash
https://api.you.com/api?subscriber[zipcode]&preview=true
```

> Example request from Drip to your endpoint during Preview As

```bash
https://api.you.com/api?subscriber[zipcode]=90210&preview=true
```

When you're either previewing or sending a test email within Drip, we will make calls to your endpoint with an additional query parameter: `preview=true`.

When you're either previewing an email or sending a test email, we won't have an Event to send to your endpoint. (And unless you're using Preview As, nor will we have a Person.) When your endpoint sees `preview=true`, we suggest sending back mocked data. This allows previews and test emails to work as expected &mdash; using your mocked data.
