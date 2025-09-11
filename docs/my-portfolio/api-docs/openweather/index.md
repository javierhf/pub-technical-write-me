---
title: My Technical Writer Portfolio
status: new
---

# OpenWeather API

{% hint style="danger" %}
**Disclaimer**\
The following pages showcase my version of some parts of the OpenWeather API documentation limited to the free plan subscription.  If you need a comprehensive documentation, please check the [official OpenWeather API documentation](https://openweathermap.org/api).\

{% endhint %}

## <mark style="color:$primary;">Overview</mark>

**OpenWeather - One Call 3.0 API provides the following information:**

* Essential weather data
* Short-term and long-term forecasts
* Aggregated weather data easily

**The OpenWeather One Call API 3.0 provides four endpoints for comprehensive weather data**. as shown in the following table:



<table><thead><tr><th width="196">Endpoint</th><th width="283">Scope</th><th>Features</th></tr></thead><tbody><tr><td><code>/onecall</code></td><td><a href="https://openweathermap.org/api/one-call-3#current"><strong>Current weather and forecasts:</strong></a></td><td><ul><li>Minute forecast for 1 hour</li><li>Hourly forecast for 48 hours</li><li>Daily forecast for 8 days</li></ul></td></tr><tr><td><code>/timemachine</code></td><td><a href="https://openweathermap.org/api/one-call-3#history"><strong>Weather data for any timestamp</strong></a></td><td>45 years historical archive and 4 days ahead forecast.</td></tr><tr><td><code>/day_summary</code></td><td><a href="https://openweathermap.org/api/one-call-3#history_daily_aggregation"><strong>Daily aggregation</strong></a></td><td>Daily aggregation of weather data for 45 years archive and 1.5 years ahead forecast.</td></tr><tr><td><code>/overview</code></td><td><a href="https://openweathermap.org/api/one-call-3#weather_overview"><strong>Weather overview</strong></a></td><td>Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies.</td></tr></tbody></table>

Based on our proprietary model, **all endpoints are updated every 10 minutes** to ensure you always have access to the most accurate and up-to-date information available in JSON, XML, or HTML format..

{% hint style="warning" %}
If you are using Dark Sky API, check our easy-to-follow[ migration process.](https://openweathermap.org/darksky-openweather-3)
{% endhint %}

## <mark style="color:$primary;">Quick Start Guide</mark>

Let's start to use the OpenWeather API by following these steps:

1. [Sign up](https://home.openweathermap.org/users/sign_up) to OpenWeather to create your account.
2. Copy your default API key (later `appid`).

_You are ready make your first API call!_

### <mark style="color:$info;">Making Your First API Call</mark>

Once you get your API key, **you can make your first API call.** We'll use the **free plan version** (One Call 2.5) to call the OpenWeather API to get our weather forecast for the following locatio&#x6E;_:_

* `lat=33.44` - Latitude
* `lon=-94.04` - Longitude

The API call will look as follows:

_`https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&appid=YOUR_API_KEY`_

&#x20;

or in CURL:

```
curl -X GET "https://api.openweathermap.org/data/2.5/weather?lat=40.7128&lon=-74.0060&appid=YOUR_API_KEY"
```

{% hint style="info" %}
**Free plan subscription limitations**\
Free plan subscriptions (version 2.5) are limited to:

* 60 calls per minute
* 5 day / 3 hour forecast data
{% endhint %}

#### **Reading Your First API Response**

{% hint style="info" %}
**Response information**

Check the [reference information](index.md#reference-information-one-call-3.0) section for a comprehensive description of the OpenWeather API production version One Call 3.0.
{% endhint %}

The API call will return all the information of the current weather information for the provided location as a **response in JSON format**:

```json
{
    "coord": {
        "lon": -94.04,
        "lat": 33.44
    },
    "weather": [
        {
            "id": 800,
            "main": "Clear",
            "description": "clear sky",
            "icon": "01n"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 293.03,
        "feels_like": 293.27,
        "temp_min": 292.59,
        "temp_max": 294.19,
        "pressure": 1019,
        "humidity": 84,
        "sea_level": 1019,
        "grnd_level": 1008
    },
    "visibility": 10000,
    "wind": {
        "speed": 0.45,
        "deg": 0,
        "gust": 0.89
    },
    "clouds": {
        "all": 0
    },
    "dt": 1757575986,
    "sys": {
        "type": 2,
        "id": 62880,
        "country": "US",
        "sunrise": 1757591833,
        "sunset": 1757636909
    },
    "timezone": -18000,
    "id": 4133367,
    "name": "Texarkana",
    "cod": 200
}
```

{% hint style="warning" %}
<mark style="color:$info;">**Empty responses**</mark>\
An API response not showing any parameters indicate that the related weather phenomena just did not happen for the data of measurement provided.

An API request without required parameters, such as latitude and longitude, will typically result in an 400 error message (nothing to show as Geocode information).
{% endhint %}

### <sub>Response Parameters</sub>

## JSON Format API Response Fields

<table><thead><tr><th>Field Path</th><th width="127">Data Type</th><th>Description</th><th>Units/Notes</th></tr></thead><tbody><tr><td><code>cod</code></td><td>Number</td><td>Internal parameter</td><td>HTTP status code</td></tr><tr><td><code>message</code></td><td>String</td><td>Internal parameter</td><td>Error message or status</td></tr><tr><td><code>cnt</code></td><td>Number</td><td>A number of timestamps returned in the API response</td><td>Count of forecast entries</td></tr><tr><td><strong>list</strong></td><td>Array</td><td>Array of forecast data objects</td><td>-</td></tr><tr><td><code>list.dt</code></td><td>Number</td><td>Time of data forecasted, unix, UTC</td><td>Unix timestamp</td></tr><tr><td><strong>list.main</strong></td><td>Object</td><td>Main weather parameters</td><td>-</td></tr><tr><td><code>list.main.temp</code></td><td>Number</td><td>Temperature</td><td>Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit</td></tr><tr><td><code>list.main.feels_like</code></td><td>Number</td><td>Human perception temperature</td><td>Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit</td></tr><tr><td><code>list.main.temp_min</code></td><td>Number</td><td>Minimum forecasted temperature</td><td>Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit</td></tr><tr><td><code>list.main.temp_max</code></td><td>Number</td><td>Maximum forecasted temperature</td><td>Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit</td></tr><tr><td><code>list.main.pressure</code></td><td>Number</td><td>Atmospheric pressure on sea level</td><td>hPa (hectopascals)</td></tr><tr><td><code>list.main.sea_level</code></td><td>Number</td><td>Atmospheric pressure on sea level</td><td>hPa (hectopascals)</td></tr><tr><td><code>list.main.grnd_level</code></td><td>Number</td><td>Atmospheric pressure on ground level</td><td>hPa (hectopascals)</td></tr><tr><td><code>list.main.humidity</code></td><td>Number</td><td>Humidity percentage</td><td>% (0-100)</td></tr><tr><td><code>list.main.temp_kf</code></td><td>Number</td><td>Internal parameter</td><td>-</td></tr><tr><td><strong>list.weather</strong></td><td>Array</td><td>Weather conditions array</td><td>-</td></tr><tr><td><code>list.weather.id</code></td><td>Number</td><td>Weather condition ID</td><td>Weather condition code</td></tr><tr><td><code>list.weather.main</code></td><td>String</td><td>Group of weather parameters</td><td>Rain, Snow, Clouds, etc.</td></tr><tr><td><code>list.weather.description</code></td><td>String</td><td>Weather condition within the group</td><td>Detailed description</td></tr><tr><td><code>list.weather.icon</code></td><td>String</td><td>Weather icon ID</td><td>Icon code (e.g., "01d")</td></tr><tr><td><strong>list.clouds</strong></td><td>Object</td><td>Cloud information</td><td>-</td></tr><tr><td><code>list.clouds.all</code></td><td>Number</td><td>Cloudiness percentage</td><td>% (0-100)</td></tr><tr><td><strong>list.wind</strong></td><td>Object</td><td>Wind information</td><td>-</td></tr><tr><td><code>list.wind.speed</code></td><td>Number</td><td>Wind speed</td><td>Default/Metric: m/s, Imperial: mph</td></tr><tr><td><code>list.wind.deg</code></td><td>Number</td><td>Wind direction</td><td>Degrees (0-360, meteorological)</td></tr><tr><td><code>list.wind.gust</code></td><td>Number</td><td>Wind gust speed</td><td>Default/Metric: m/s, Imperial: mph</td></tr><tr><td><code>list.visibility</code></td><td>Number</td><td>Average visibility</td><td>Meters (max: 10,000m)</td></tr><tr><td><code>list.pop</code></td><td>Number</td><td>Probability of precipitation</td><td>Decimal (0.0-1.0, where 1.0 = 100%)</td></tr><tr><td><strong>list.rain</strong></td><td>Object</td><td>Rain information (optional)</td><td>-</td></tr><tr><td><code>list.rain.3h</code></td><td>Number</td><td>Rain volume for last 3 hours</td><td>mm (millimeters)</td></tr><tr><td><strong>list.snow</strong></td><td>Object</td><td>Snow information (optional)</td><td>-</td></tr><tr><td><code>list.snow.3h</code></td><td>Number</td><td>Snow volume for last 3 hours</td><td>mm (millimeters)</td></tr><tr><td><strong>list.sys</strong></td><td>Object</td><td>System parameters</td><td>-</td></tr><tr><td><code>list.sys.pod</code></td><td>String</td><td>Part of the day</td><td>"n" (night) or "d" (day)</td></tr><tr><td><code>list.dt_txt</code></td><td>String</td><td>Time of data forecasted</td><td>ISO 8601 format, UTC</td></tr><tr><td><strong>city</strong></td><td>Object</td><td>City information</td><td>-</td></tr><tr><td><code>city.id</code></td><td>Number</td><td>City ID</td><td>Numeric identifier (deprecated)</td></tr><tr><td><code>city.name</code></td><td>String</td><td>City name</td><td>City name (deprecated)</td></tr><tr><td><strong>city.coord</strong></td><td>Object</td><td>City coordinates</td><td>-</td></tr><tr><td><code>city.coord.lat</code></td><td>Number</td><td>Geo location latitude</td><td>Decimal degrees (-90 to 90)</td></tr><tr><td><code>city.coord.lon</code></td><td>Number</td><td>Geo location longitude</td><td>Decimal degrees (-180 to 180)</td></tr><tr><td><code>city.country</code></td><td>String</td><td>Country code</td><td>ISO 3166 country code (e.g., "US", "GB")</td></tr><tr><td><code>city.population</code></td><td>Number</td><td>City population</td><td>Number of inhabitants</td></tr><tr><td><code>city.timezone</code></td><td>Number</td><td>Shift in seconds from UTC</td><td>Seconds offset from UTC</td></tr><tr><td><code>city.sunrise</code></td><td>Number</td><td>Sunrise time</td><td>Unix timestamp, UTC</td></tr><tr><td><code>city.sunset</code></td><td>Number</td><td>Sunset time</td><td>Unix timestamp, UTC</td></tr></tbody></table>

### <mark style="color:$info;">How to Exclude Parts of the Weather Forecast</mark>

You can make an API exluding parts of the weather forecast as shown in the follwing example:

```
https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&exclude=hourly,daily&appid=YOUR_API_KEY
```

<mark style="color:$info;">or in CURL:</mark>

```
curl -X GET "https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&exclude=hourly,daily&appid=YOUR_API_KEY"
```

### <mark style="color:$info;">Getting New API Keys</mark>

Whenever you need a new API key, follow theses steps:

1. In your OpenWeather home page, navigate to the [API keys](https://home.openweathermap.org/api_keys) tab.
2. Under **Create key**, provide a name of the API key.   &#x20;
3. Click **Generate.**

### <mark style="color:$info;">Authentication and Authorization</mark>

<mark style="color:$info;">The OpenWeather API uses API keys authentication.</mark> <mark style="color:$info;"></mark><mark style="color:$info;">**Include your API key in every request**</mark> <mark style="color:$info;"></mark><mark style="color:$info;">as follows:</mark>

```
https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&appid=YOUR_API_KEY
```

1. [**Sign up**](https://home.openweathermap.org/users/sign_up) **to OpenWeather.** &#x20;
2. Create an [**OpenWeather API key**](https://home.openweathermap.org/api_keys).

### _<mark style="color:$info;">API Keys and API Call Limit</mark>_

You can **generate as many API keys as you need** for your subscription; we'll track the total usage across all of them.

The One Call API 3.0 has a **default limit of 2,000 calls per day**. To change this limit, navigate to the  ["your account billing plans"](https://home.openweathermap.org/subscriptions) tab and update the standard settings.&#x20;

{% hint style="info" %}
**Call limits and billing plans**\
Learn more about our call limits and billing plans in the [reference section](index.md#api-keys-and-api-call-limit-1).
{% endhint %}

***

## <mark style="color:$primary;">Reference Information (One Call 3.0)</mark>

### Overview

**OpenWeather - One Call 3.0 API provides the following information:**

* Essential weather data
* Short-term and long-term forecasts
* Aggregated weather data easily

**The OpenWeather One Call API 3.0 provides four endpoints for comprehensive weather data**. as shown in the following table:



<table><thead><tr><th width="196">Endpoint</th><th width="283">Scope</th><th>Features</th></tr></thead><tbody><tr><td><code>/onecall</code></td><td><a href="https://openweathermap.org/api/one-call-3#current"><strong>Current weather and forecasts:</strong></a></td><td><ul><li>Minute forecast for 1 hour</li><li>Hourly forecast for 48 hours</li><li>Daily forecast for 8 days</li></ul></td></tr><tr><td><code>/timemachine</code></td><td><a href="https://openweathermap.org/api/one-call-3#history"><strong>Weather data for any timestamp</strong></a></td><td>45 years historical archive and 4 days ahead forecast.</td></tr><tr><td><code>/day_summary</code></td><td><a href="https://openweathermap.org/api/one-call-3#history_daily_aggregation"><strong>Daily aggregation</strong></a></td><td>Daily aggregation of weather data for 45 years archive and 1.5 years ahead forecast.</td></tr><tr><td><code>/overview</code></td><td><a href="https://openweathermap.org/api/one-call-3#weather_overview"><strong>Weather overview</strong></a></td><td>Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies.</td></tr></tbody></table>

Based on our proprietary model, **all endpoints are updated every 10 minutes** to ensure you always have access to the most accurate and up-to-date information available in JSON, XML, or HTML format..

{% hint style="warning" %}
If you are using Dark Sky API, check our easy-to-follow[ migration process.](https://openweathermap.org/darksky-openweather-3)
{% endhint %}

### _<mark style="color:$info;">API Keys and API Call Limit</mark>_

You can **generate as many API keys as you need** for your subscription; we'll track the total usage across all of them.

The One Call API 3.0 has a **default limit of 2,000 calls per day**. To change this limit, navigate to the  ["your account billing plans"](https://home.openweathermap.org/subscriptions) tab and update the standard settings.&#x20;

ADD HERE AL INFO

### <mark style="color:$info;">Endpoints and Methods</mark>

{% hint style="info" %}
<mark style="color:$info;">**One Call 3.0**</mark>\
Please note that One Call 3.0 is included in the One Call by Call subscription _ONLY_. [Learn more](https://openweathermap.org/price).
{% endhint %}

**The root URL for the API** is [https://api.openweathermap.org/data/3.0/onecall](https://api.openweathermap.org/data/3.0/opencall). In the following sections you will learn more about the One Call API 3.0 methods and endpoints.

#### _**`/onecall`**_

_Current and forecast data._

**GET** [https://api.openweathermap.org/data/3.0/onecall](https://api.openweathermap.org/data/3.0/onecall)

<mark style="color:orange;">**Parameters**</mark>

<table><thead><tr><th width="120">Name</th><th width="102">Required</th><th width="109">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>lat</strong></td><td><em>Yes</em></td><td>float</td><td>Latitude, decimal (-90; 90).<br><br>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</td></tr><tr><td><strong>lon</strong></td><td><em>Yes</em></td><td>float</td><td>Longitude, decimal (-180; 180). <br><br>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</td></tr><tr><td><strong>appid</strong></td><td><em>Yes</em></td><td>string</td><td>Your unique API key (you can always find it on your account page under the "API key" tab).</td></tr><tr><td><strong>exclude</strong></td><td><em>No</em></td><td>list</td><td><p>By using this parameter you can exclude some parts of the weather data from the API response. <br><br>Comma-delimited list (without spaces). </p><p><br>Available values: <em>current, minutely, hourly, daily, and alerts.</em></p></td></tr><tr><td><strong>units</strong></td><td><em>No</em></td><td>string</td><td><p>Units of measurement.</p><p></p><p>Available values: <em>standard, metrics, imperial.</em><br><br>If the <em>units</em> parameter is left empty, the standard units measure will be applied by default.</p></td></tr><tr><td><strong>lang</strong></td><td><em>No</em></td><td>string</td><td>You can use the <em>lang</em> parameter to get the output in your language.</td></tr></tbody></table>

<mark style="color:orange;">**Request Example**</mark>\
`https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}`

<mark style="color:orange;">**Response Example**</mark>

```json
{

`   `"lat": 51.509865,

`   `"lon": -0.118092,

`   `"tz": "+01:00",

`   `"date": "2024-05-13",

`   `"units": "metric",

`   `"weather\_overview": "The current weather is overcast with a 

temperature of 16°C and a feels-like temperature of 16°C. 

The wind speed is 4 meter/sec with gusts up to 6 meter/sec 

coming from the west-southwest direction. 

The air pressure is at 1007 hPa with a humidity level of 79%. 

The dew point is at 12°C and the visibility is 10000 meters. 

The UV index is at 4, indicating moderate risk from the 

sun's UV rays. 

The sky is covered with overcast clouds, and there is no precipitation expected at the moment. Overall, it is a moderately cool and cloudy day with light to moderate winds from the west-southwest."

}
```

#### _**`/timemachine`**_

_Weather data for timestamp_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/timemachine](https://api.openweathermap.org/data/3.0/onecall/timemachine)

<mark style="color:orange;">**Parameters**</mark>

<table><thead><tr><th width="96">Name</th><th width="117">Required</th><th width="140">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>lat</strong></td><td><em>Yes</em></td><td>float</td><td><p>Latitude, decimal (-90; 90).</p><p> </p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>lon</strong></td><td><em>Yes</em></td><td>float</td><td><p>Longitude, decimal (-180; 180). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>appid</strong></td><td><em>Yes</em></td><td>string</td><td>Your unique API key (you can always find it on your account page under the "API key" tab).</td></tr><tr><td><strong>dt</strong></td><td><em>Yes</em></td><td>integer</td><td><p>Timestamp (Unix time, UTC time zone), e.g. dt=1586468027. </p><p>Data is available from January 1st, 1979 till 4 days ahead.</p></td></tr><tr><td><strong>units</strong></td><td>No</td><td>string</td><td>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. </td></tr><tr><td><strong>lang</strong></td><td>No</td><td>string</td><td>You can use the <em>lang</em> parameter to get the output in your language. </td></tr></tbody></table>

<mark style="color:orange;">**Request Example**</mark>

`https://api.openweathermap.org/data/3.0/onecall?lat=33.44&lon=-94.04&appid={API key}`

<mark style="color:orange;">**Response Example**</mark>

```json
{

`   `"lat":33.44,

`   `"lon":-94.04,

`   `"timezone":"America/Chicago",

`   `"timezone\_offset":-18000,

`   `"current":{

`      `"dt":1684929490,

`      `"sunrise":1684926645,

`      `"sunset":1684977332,

`      `"temp":292.55,

`      `"feels\_like":292.87,

`      `"pressure":1014,

`      `"humidity":89,

`      `"dew\_point":290.69,

`      `"uvi":0.16,

`      `"clouds":53,

`      `"visibility":10000,

`      `"wind\_speed":3.13,

`      `"wind\_deg":93,

`      `"wind\_gust":6.71,

`      `"weather":[

`         `{

`            `"id":803,

`            `"main":"Clouds",

`            `"description":"broken clouds",

`            `"icon":"04d"

`         `}

`      `]

`   `},

`   `"minutely":[

`      `{

`         `"dt":1684929540,

`         `"precipitation":0

`      `},

...

`   `],

`   `"hourly":[

`      `{

`         `"dt":1684926000,

`         `"temp":292.01,

`         `"feels\_like":292.33,

`         `"pressure":1014,

`         `"humidity":91,

`         `"dew\_point":290.51,

`         `"uvi":0,

`         `"clouds":54,

`         `"visibility":10000,

`         `"wind\_speed":2.58,

`         `"wind\_deg":86,

`         `"wind\_gust":5.88,

`         `"weather":[

`            `{

`               `"id":803,

`               `"main":"Clouds",

`               `"description":"broken clouds",

`               `"icon":"04n"

`            `}

`         `],

`         `"pop":0.15

`      `},

...

`   `],

`   `"daily":[

`      `{

`         `"dt":1684951200,

`         `"sunrise":1684926645,

`         `"sunset":1684977332,

`         `"moonrise":1684941060,

`         `"moonset":1684905480,

`         `"moon\_phase":0.16,

`         `"summary":"Expect a day of partly cloudy with rain",

`         `"temp":{

`            `"day":299.03,

`            `"min":290.69,

`            `"max":300.35,

`            `"night":291.45,

`            `"eve":297.51,

`            `"morn":292.55

`         `},

`         `"feels\_like":{

`            `"day":299.21,

`            `"night":291.37,

`            `"eve":297.86,

`            `"morn":292.87

`         `},

`         `"pressure":1016,

`         `"humidity":59,

`         `"dew\_point":290.48,

`         `"wind\_speed":3.98,

`         `"wind\_deg":76,

`         `"wind\_gust":8.92,

`         `"weather":[

`            `{

`               `"id":500,

`               `"main":"Rain",

`               `"description":"light rain",

`               `"icon":"10d"

`            `}

`         `],

`         `"clouds":92,

`         `"pop":0.47,

`         `"rain":0.15,

`         `"uvi":9.23

`      `},

...

`   `],

`    `"alerts": [

`    `{

`      `"sender\_name": "NWS Philadelphia - Mount Holly (New Jersey, Delaware, Southeastern Pennsylvania)",

`      `"event": "Small Craft Advisory",

`      `"start": 1684952747,

`      `"end": 1684988747,

`      `"description": "...SMALL CRAFT ADVISORY REMAINS IN EFFECT FROM 5 PM THIS\nAFTERNOON TO 3 AM EST FRIDAY...\n\* WHAT...North winds 15 to 20 kt with gusts up to 25 kt and seas\n3 to 5 ft expected.\n\* WHERE...Coastal waters from Little Egg Inlet to Great Egg\nInlet NJ out 20 nm, Coastal waters from Great Egg Inlet to\nCape May NJ out 20 nm and Coastal waters from Manasquan Inlet\nto Little Egg Inlet NJ out 20 nm.\n\* WHEN...From 5 PM this afternoon to 3 AM EST Friday.\n\* IMPACTS...Conditions will be hazardous to small craft.",

`      `"tags": [

`      `]

`    `},

...

`  `]  

```

#### _**`/day_summary`**_

_Aggregated weather data for a particular date from 2nd January 1979 till long-term forecast for 1,5 years ahead_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/day\_summary](https://api.openweathermap.org/data/3.0/onecall/day_summary)

<mark style="color:orange;">**Parameters**</mark>

<table><thead><tr><th width="119">Name</th><th width="118">Required</th><th width="160">Description</th><th>Description</th></tr></thead><tbody><tr><td><strong>lat</strong></td><td><em>Yes</em></td><td>float</td><td><p>Latitude, decimal (-90; 90). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>lon</strong></td><td><em>Yes</em></td><td>float</td><td><p>Longitude, decimal (-180; 180). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>appid</strong></td><td><em>Yes</em></td><td>string</td><td>Your unique API key (you can always find it on your account page under the "API key" tab).</td></tr><tr><td><strong>date</strong></td><td><em>Yes</em></td><td>string</td><td><p>Date in the <code>YYYY-MM-DD</code> format for which data is requested. </p><p></p><p>Date is available for 45 years archive (starting from 1979-01-02) up to the 1,5 years ahead forecast to the current date.</p></td></tr><tr><td><strong>units</strong></td><td><em>No</em></td><td>string</td><td>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. </td></tr><tr><td><strong>lang</strong></td><td><em>No</em></td><td>string</td><td>You can use the <em>lang</em> parameter to get the output in your language. </td></tr></tbody></table>

<mark style="color:orange;">**Request Example**</mark>

`https://api.openweathermap.org/data/3.0/onecall/day_summary?lat=39.099724&lon=-94.578331&date=2020-03-04&appid={API key}`

<mark style="color:orange;">**Response Example**</mark>

```json

{

`   `"lat":33,

`   `"lon":35,

`   `"tz":"+02:00",

`   `"date":"2020-03-04",

`   `"units":"standard",

`   `"cloud\_cover":{

`      `"afternoon":0

`   `},

`   `"humidity":{

`      `"afternoon":33

`   `},

`   `"precipitation":{

`      `"total":0

`   `},

`   `"temperature":{

`      `"min":286.48,

`      `"max":299.24,

`      `"afternoon":296.15,

`      `"night":289.56,

`      `"evening":295.93,

`      `"morning":287.59

`   `},

`   `"pressure":{

`      `"afternoon":1015

`   `},

`   `"wind":{

`      `"max":{

`         `"speed":8.7,

`         `"direction":120

`      `}

}  
```

#### _**`/overview`**_

_Weather overview information with a human-readable weather summary for today and tomorrow’s forecast, utilizing OpenWeather AI technologies_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/overview](https://api.openweathermap.org/data/3.0/onecall/overview)

<mark style="color:orange;">**Parameters**</mark>

<table><thead><tr><th width="119">Name</th><th width="103">Required</th><th width="171">Type</th><th>Description</th></tr></thead><tbody><tr><td><strong>lat</strong></td><td><em>Yes</em></td><td>float</td><td><p>Latitude, decimal (-90; 90). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>lon</strong></td><td><em>Yes</em></td><td>float</td><td><p>Longitude, decimal (-180; 180). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API.</p></td></tr><tr><td><strong>appid</strong></td><td><em>Yes</em></td><td>string</td><td>Your unique API key (you can always find it on your account page under the "API key" tab)</td></tr><tr><td><strong>date</strong></td><td><em>No</em></td><td>string</td><td><p>The date the user wants to get a weather summary in the YYYY-MM-DD format. Data is available for today and tomorrow. </p><p></p><p>If not specified, the current date will be used by default.<br><br>Please note that the date is determined by the timezone relevant to the coordinates specified in the API request.</p></td></tr><tr><td><strong>units</strong></td><td><em>No</em></td><td>string</td><td>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. </td></tr><tr><td><strong>lang</strong></td><td><em>No</em></td><td>string</td><td>You can use the <em>lang</em> parameter to get the output in your language. </td></tr></tbody></table>

<mark style="color:orange;">**Request Example**</mark>

_`https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}`_

<mark style="color:orange;">**Response Example**</mark>

```json
 {

`   `"lat": 51.509865,

`   `"lon": -0.118092,

`   `"tz": "+01:00",

`   `"date": "2024-05-13",

`   `"units": "metric",

`   `"weather\_overview": "The current weather is overcast with a 

temperature of 16°C and a feels-like temperature of 16°C. 

The wind speed is 4 meter/sec with gusts up to 6 meter/sec 

coming from the west-southwest direction. 

The air pressure is at 1007 hPa with a humidity level of 79%. 

The dew point is at 12°C and the visibility is 10000 meters. 

The UV index is at 4, indicating moderate risk from the 

sun's UV rays. 

The sky is covered with overcast clouds, and there is 

no precipitation expected at the moment. 

Overall, it is a moderately cool and cloudy day 

with light to moderate winds from the west-southwest."

}  

```



### <mark style="color:$info;">Errors and Error Handling Error</mark>

Opencall 3.0 handles 401, 400, 429, and 5xx error codes. Error response payload returned for all types of errors has the following structure:

```json
{

`    `"cod":400,                          # Error code

`    `"message":"Invalid date format", # Error description

`    `"parameters": [                   # List of request parameters name related to the error

`        `"date"

`    `]

}  
```

#### _**Error Codes**_

Check the following table for more information about the status and error codes:

<table><thead><tr><th width="180">Error Code</th><th>Description</th></tr></thead><tbody><tr><td><strong>400</strong></td><td>Nothing to show as Geocode information.</td></tr><tr><td><strong>401</strong></td><td><p>Unauthorized. You can get 401 error if API token did not provided in the request or in case API token provided in the request does not grant access to this API.</p><p></p><p>You must add API token with granted access to the product to the request before returning it.</p></td></tr><tr><td><strong>404</strong></td><td><p>Not Found. You can get 404 error if data with requested parameters (lat, lon, date etc) does not exist in service database.</p><p></p><p>You must not retry the same request.</p></td></tr><tr><td><strong>429</strong></td><td><p>Too Many Requests. You can get 429 error if the key quota of requests for the provided API to this API was exceeded.</p><p></p><p>You may retry the request after some time or after extending your key quota.</p></td></tr><tr><td><strong>5xx</strong></td><td><p>Unexpected Error. You can get '5xx' error in case of other internal errors. Error Response code will be <code>5xx</code>.</p><p></p><p>Please contact us and enclose an example of your API request that receives this error in your email to let us analyse it and find a solution for you promptly.</p><p></p><p>You may retry the request which led to this error.</p></td></tr></tbody></table>

## <mark style="color:$primary;">Best Practices</mark>

**The following table provides the best practices** that allow you to get the most out of the OpenWeather API:

<table><thead><tr><th width="255">Scope</th><th>Best Practice</th></tr></thead><tbody><tr><td><strong>API Key Management</strong></td><td><p>Securely store your API key. Do not hardcode it in your application's source code, especially if the code is publicly accessible.</p><p></p><p>Use environment variables or secure app settings for API key management.</p></td></tr><tr><td><strong>Efficient Use of API Calls</strong></td><td><p>To avoid reaching your API call limit, cache responses whenever possible, especially if you're requesting data that doesn't change frequently.</p><p></p><p>OpenWeather data updates every 10 minutes, so plan your requests accordingly.</p></td></tr><tr><td><strong>Use the Correct Endpoint</strong></td><td><p>OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.).</p><p></p><p>Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p></td></tr><tr><td><strong>Use the Correct Endpoint</strong></td><td><p>OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.).</p><p></p><p>Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p></td></tr><tr><td><strong>Handle Errors Gracefully</strong></td><td><p>Implement error handling in your application to manage API request failures or unexpected responses.</p><p></p><p>This includes handling HTTP status codes and parsing error messages returned by the API.</p></td></tr><tr><td><strong>Optimize Requests with Parameters</strong></td><td>Use API request parameters effectively to get only the data you need. For example, you can exclude parts of the data you don't need with the exclude parameter in the One Call API 3.0.</td></tr><tr><td><strong>Respect API Limits</strong></td><td><p>Be aware of your subscription plan's API call limits and ensure your application does not exceed them. </p><p></p><p>Implement logic to throttle requests if necessary.</p></td></tr><tr><td><strong>Use Units and Language Parameters</strong></td><td>Customize API responses for your audience by using the units parameter to specify temperature and wind speed units, and the lang parameter to localize weather descriptions.</td></tr><tr><td><strong>Geocoding</strong></td><td>Use the Geocoding API to convert between city names and geographical coordinates when necessary, as direct requests by city name may be deprecated for some endpoints.</td></tr><tr><td><strong>Subscription Management</strong></td><td><p>Keep track of your subscription status and the features available to you. </p><p></p><p>Some features, like the One Call API 3.0, require a separate subscription.</p></td></tr><tr><td><strong>Stay Updated</strong></td><td><p>OpenWeather periodically updates its APIs and documentation. </p><p></p><p>Stay informed about any changes that might affect your application by regularly checking the OpenWeather website or subscribing to their updates.</p></td></tr></tbody></table>

## <mark style="color:$primary;">Glossary</mark>

> <mark style="color:blue;">**A**</mark>

* **API Key:**\
  A unique and required identifier to authenticate requests to the OpenWeather API. It's provided when you create an account on OpenWeather.
* **Accumulated Parameters**: \
  Data that represents the accumulation of weather elements, such as precipitation, over a specified period.
* **Air Pollution API**:\
  Provides data on air quality, including concentrations of pollutants like CO, NO2, and PM2.5, for any specified location.

> <mark style="color:blue;">**B**</mark>

* **Bulk Downloading**: \
  A feature that allows downloading large datasets of current weather or forecasts in JSON format, available for certain account types.

> <mark style="color:blue;">**C**</mark>

* **Callback Function**: \
  Used in JavaScript to handle asynchronous operations, such as receiving data from the API.
* **Climatic Forecast 30 Days**: \
  A long-term weather forecast that gives a general idea of the weather conditions for the coming month.
* **Current Weather Data**: \
  Real-time weather information for any location on Earth, including temperature, humidity, pressure, and more.

> <mark style="color:blue;">**D**</mark>

* **Daily Forecast 16 Days**: \
  A weather forecast service that provides daily weather data, including temperature and weather conditions, for up to 16 days ahead.

> <mark style="color:blue;">**H**</mark>

* **Hourly Forecast 4 Days**: \
  A detailed forecast that provides weather data in 3-hour intervals for up to 4 days ahead.
* **History API**: \
  Provides historical weather data for any location on Earth. Useful for analyzing past weather conditions.

> <mark style="color:purple;">**F**</mark>

* **5 Day / 3 Hour Forecast**: \
  A five-day weather forecast with details provided every three hours.
* **Fire Weather Index API**: \
  Offers information related to the risk of wildfire, which can be critical for fire prevention efforts in vulnerable areas.

> <mark style="color:purple;">**G**</mark>

* **Geocoding API**: Converts between addresses (like city names) and geographic coordinates (latitude and longitude), and vice versa.

> <mark style="color:purple;">**J**</mark>

* **JSON/XML Format**: \
  The formats in which API responses can be received. JSON is the default format, but XML is also available for most data types.

> <mark style="color:purple;">**M**</mark>

* **Multilingual Support**: \
  The API can return data in multiple languages, making it accessible to a global audience.

> <mark style="color:purple;">**S**</mark>

* **Statistical Weather Data API**: \
  Offers statistical data based on historical weather information, which can be used for research and analysis.

> <mark style="color:orange;">**U**</mark>

* **Units of Measurement**: \
  The API supports standard (Kelvin, meters/sec), metric (Celsius, meters/sec), and imperial (Fahrenheit, miles/hour) units for temperature, wind speed, and other measurements.

> <mark style="color:orange;">**W**</mark>

* **Weather Maps 2.0**: \
  A service that provides various weather maps, including forecast, historical, and current weather maps, which can be integrated into web and mobile applications.
