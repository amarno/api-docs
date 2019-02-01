# Preview/Test Mode

> Example request from Drip to your endpoint during Preview/Test

```bash
https://api.you.com/api?subscriber[zipcode]&preview=true
```

> Example request from Drip to your endpoint during Preview As

```bash
https://api.you.com/api?subscriber[zipcode]=90210&preview=true
```

When previewing or sending a test email within Drip, we’ll make calls to your endpoint with an additional query parameter: `preview=true`.

When that happens, we suggest your endpoint send back mocked data. This allows preview and test emails to populate with sample content for a more accurate experience.

This is because in these contexts we won't have an Event to send to your endpoint. (And unless you're using Preview As, nor will we have a Person.)
