# Example

> Example request from Drip to your endpoint

```bash
https://api.you.com/api?subscriber[zipcode]=90210
```

> Example response from Drip's [weather service](https://github.com/DripEmail/custom-dynamic-weather)

```json
{
    "apparentTemperature": 65.89,
    "cloudCover": 0.09,
    "dewPoint": 22.55,
    "humidity": 0.19,
    "icon": "clear-night",
    "nearestStormBearing": 131,
    "nearestStormDistance": 446,
    "ozone": 258.97,
    "precipIntensity": 0,
    "precipProbability": 0,
    "pressure": 1018.59,
    "summary": "Clear",
    "temperature": 65.89,
    "time": 1541727521,
    "uvIndex": 0,
    "visibility": 8.27,
    "windBearing": 1,
    "windGust": 10.09,
    "windSpeed": 4.39
}
```

Imagine that you've got a service that returns the weather for a given zipcode. As a canonical example, have a look at our [weather service](https://github.com/DripEmail/custom-dynamic-weather).

Now, consider some Custom Dynamic Content that looks like this:

`Good morning {{ subscriber.first_name }}! Looks like it's {{ my.weather.summary | downcase }} in your neck of the woods!`

At the point that we render this content, we'll make a request to your API. If you're using our [weather service](https://github.com/DripEmail/custom-dynamic-weather), the request and response will look something like what you see to the right.

In addition to having access to the `subscriber` object, all of your Custom Dynamic Content will be available in a `my` object. In this example, we're making the response above available as `my.weather`.

And so, when the Liquid is rendered, it might look like:

`Good morning Mary! Looks like it's clear in your neck of the woods!`
