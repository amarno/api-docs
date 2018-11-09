# Background

Custom Dynamic Content allows you to pull data from your system into Drip emails. Your data is then available
via Liquid, allowing you to build super-rich personalized emails augmented with fresh data from your own systems.

Example use cases:

- Is it going to rain this weekend? Offer your customer an umbrella! Or maybe it'll be sunny? Show them a hat!
- Show up-to-date prices for a flight or ticketed event for which a customer is interested! Drip can pass customer information to your endpoint, and pull in the latest prices.

## How it works

1. You provide an API endpoint
1. You choose the Liquid shortcode
1. When we render an email, we'll `GET` a JSON document from your endpoint
1. You'll then have access to that document in Liquid via your shourcode

See [Drip Weather](https://github.com/DripEmail/drip-personalized-weather) as an example endpoint.
