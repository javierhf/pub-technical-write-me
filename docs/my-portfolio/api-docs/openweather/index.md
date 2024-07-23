---
title: My Technical Writer Portfolio
status: new
---

# OpenWeather API

> **Disclaimer:**\
> The sole purpose of this page is to showcase my technical writing skills by applying my ideas and experience to the Openweather - One Call 3.0 API public documentation. \
> No criticism is intended.\
> **Tools**\
> _Markdown, GitHub, GitBook_

## Original Content

[One Call API 3.0](https://docs.openweather.co.uk/api/one-call-3)

## My Version

### Reference Documentation

**OpenWeather - One Call 3.0 API provides essential weather data, short-term and long-term forecasts, and aggregated weather data** easily via our One Call API 3.0.

**One Call API 3.0 is based on the proprietary OpenWeather Model and provides 4 endpoints.** Our endpoints are updated every 10 minutes to deliver the most accurate and up-to-date weather data.

#### OpenWeather One Call API 3.0 Endpoints

**One Call API 3.0 contains 4 endpoints**, providing access to various data as shown in the following table:

<table><thead><tr><th width="250">Endpoint</th><th>Scope</th><th>Features</th></tr></thead><tbody><tr><td><code>/onecall</code></td><td><a href="https://openweathermap.org/api/one-call-3#current"><strong>Current weather and forecasts:</strong></a></td><td><ul><li>Minute forecast for 1 hour</li><li>Hourly forecast for 48 hours</li><li>Daily forecast for 8 days</li></ul></td></tr><tr><td><code>/timemachine</code></td><td><a href="https://openweathermap.org/api/one-call-3#history"><strong>Weather data for any timestamp</strong></a></td><td>45 years historical archive and 4 days ahead forecast</td></tr><tr><td><code>/day_summary</code></td><td><a href="https://openweathermap.org/api/one-call-3#history_daily_aggregation"><strong>Daily aggregation</strong></a></td><td>Daily agreggation of weather data for 45 years archive and 1.5 years ahead forecast</td></tr><tr><td><code>/overview</code></td><td><a href="https://openweathermap.org/api/one-call-3#weather_overview"><strong>Weather overview</strong></a></td><td>Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies</td></tr></tbody></table>

> _Note:_ Data is available in JSON, XML, or HTML format



{% hint style="warning" %}
If you are using Dark Sky API, check our easy-to-follow[ migration process.](https://openweathermap.org/darksky-openweather-3)
{% endhint %}

#### _API Keys and Default API Calls_

**You can generate as many API keys as needed for your subscription.** We track the total usage from all of them.

**One Call API 3.0 sets a default limit of 2000 API calls per day**. If you need to change this limit, please check the information in the ["your account billing plans"](https://home.openweathermap.org/subscriptions) tab and update the standard settings. For more information, read our documentation page.

#### Resources Description (Methods and Endpoints)

{% hint style="info" %}
Please note that One Call 3.0 is included in the "One Call by Call" subscription **only**. [Learn more](https://openweathermap.org/price).

GET is the only HTTP method available for all resources. The root url for the API is [https://api.openweathermap.org/data/3.0/](https://api.openweathermap.org/data/3.0/)opencall.
{% endhint %}



_**`/onecall`**_

_Current and forecast data._

**GET** [https://api.openweathermap.org/data/3.0/onecall](https://api.openweathermap.org/data/3.0/onecall)

**Parameters**

| Name        | Required | Description                                                                                                                                                                                                                                            |
| ----------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **lat**     | _Yes_    | <p>Latitude, decimal (-90; 90).<br><br>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                                                            |
| **lon**     | _Yes_    | <p>Longitude, decimal (-180; 180). <br><br>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                                                        |
| **appid**   | _Yes_    | Your unique API key (you can always find it on your account page under the "API key" tab)                                                                                                                                                              |
| **exclude** | _No_     | <p>By using this parameter you can exclude some parts of the weather data from the API response. <br><br>It should be a comma-delimited list (without spaces). </p><p><br>Available values: <em>current, minutely, hourly, daily, and alerts.</em></p> |
| **units**   | _No_     | <p>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default.</p>                                           |
| **lang**    | _No_     | You can use the _lang_ parameter to get the output in your language. Learn more                                                                                                                                                                        |

**Request Example**\
`https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}`

**Response Example**

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

_**`/timemachine`**_

_Weather data for timestamp_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/timemachine](https://api.openweathermap.org/data/3.0/onecall/timemachine)

**Parameters**

| Name      | Required | Description                                                                                                                                                                                                             |
| --------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **lat**   | _Yes_    | <p>Latitude, decimal (-90; 90).</p><p> </p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                      |
| **lon**   | _Yes_    | <p>Longitude, decimal (-180; 180). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                   |
| **appid** | _Yes_    | Your unique API key (you can always find it on your account page under the "API key" tab)                                                                                                                               |
| **dt**    | _Yes_    | <p>Timestamp (Unix time, UTC time zone), e.g. dt=1586468027. </p><p>Data is available from January 1st, 1979 till 4 days ahead</p>                                                                                      |
| **units** | No       | <p>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. Learn more</p> |
| **lang**  | No       | You can use the _lang_ parameter to get the output in your language.                                                                                                                                                    |

**Request Example**

`https://api.openweathermap.org/data/3.0/onecall?lat=33.44&lon=-94.04&appid={API key}`

**Response Example**

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

_**`/day_summary`**_

_Agreggated weather data for a particular date from 2nd January 1979 till long-term forecast for 1,5 years ahead_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/day\_summary](https://api.openweathermap.org/data/3.0/onecall/day\_summary)

**Parameters**

| Name      | Required | Description                                                                                                                                                                                                           |
| --------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **lat**   | _Yes_    | <p>Latitude, decimal (-90; 90). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                    |
| **lon**   | _Yes_    | <p>Longitude, decimal (-180; 180). </p><p></p><p>If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API</p>                 |
| **appid** | _Yes_    | Your unique API key (you can always find it on your account page under the "API key" tab)                                                                                                                             |
| **datet** | _Yes_    | <p>Date in the <code>YYYY-MM-DD</code> format for which data is requested. </p><p></p><p>Date is available for 45 years archive (starting from 1979-01-02) up to the 1,5 years ahead forecast to the current date</p> |
| **units** | _No_     | <p>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. </p>         |
| **lang**  | _No_     | You can use the _lang_ parameter to get the output in your language.                                                                                                                                                  |

**Request Example**

`https://api.openweathermap.org/data/3.0/onecall/day_summary?lat=39.099724&lon=-94.578331&date=2020-03-04&appid={API key}`

**Response Example**

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

_**`/overview`**_

_Weather overview information with a human-readable weather summary for today and tomorrow’s forecast, utilizing OpenWeather AI technologies_.

**GET** [https://api.openweathermap.org/data/3.0/onecall/overview](https://api.openweathermap.org/data/3.0/onecall/overview)

**Parameters**

| Name      | Required | Description                                                                                                                                                                                                                                                                                                     |
| --------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **lat**   | _Yes_    | Latitude, decimal (-90; 90). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API                                                                                                                                   |
| **lon**   | _Yes_    | Longitude, decimal (-180; 180). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API                                                                                                                                |
| **appid** | _Yes_    | Your unique API key (you can always find it on your account page under the "API key" tab)                                                                                                                                                                                                                       |
| **datet** | _No_     | <p>The date the user wants to get a weather summary in the YYYY-MM-DD format. Data is available for today and tomorrow. If not specified, the current date will be used by default.<br><br>Please note that the date is determined by the timezone relevant to the coordinates specified in the API request</p> |
| **units** | _No_     | <p>Units of measurement. <em>standard</em>, <em>metric</em> and <em>imperial</em> units are available.<br><br>If you do not use the <em>units</em> parameter, standard units will be applied by default. Learn more</p>                                                                                         |
| **lang**  | _No_     | You can use the _lang_ parameter to get the output in your language. Learn more                                                                                                                                                                                                                                 |

**Request Example**

_`https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}`_

**Response Example**

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

### Conceptual Documentation

**OpenWeather - One Call 3.0 API provides essential weather data, short-term and long-term forecasts, and aggregated weather data** easily via our One Call API 3.0.

**One Call API 3.0 is based on the proprietary OpenWeather Model and provides 4 endpoints.** Our endpoints are updated every 10 minutes to deliver the most accurate and up-to-date weather data.

#### OpenWeather One Call API 3.0 Endpoints

**One Call API 3.0 contains 4 endpoints**, providing access to various data as shown in the following table:

<table><thead><tr><th width="198">Endpoint</th><th>Scope</th><th>Features</th></tr></thead><tbody><tr><td><code>/onecall</code></td><td><a href="https://openweathermap.org/api/one-call-3#current"><strong>Current weather and forecasts:</strong></a></td><td><ul><li>Minute forecast for 1 hour</li><li>Hourly forecast for 48 hours</li><li>Daily forecast for 8 days</li></ul></td></tr><tr><td><code>/timemachine</code></td><td><a href="https://openweathermap.org/api/one-call-3#history"><strong>Weather data for any timestamp</strong></a></td><td>45 years historical archive and 4 days ahead forecast.</td></tr><tr><td><code>/day_summary</code></td><td><a href="https://openweathermap.org/api/one-call-3#history_daily_aggregation"><strong>Daily aggregation</strong></a></td><td>Daily agreggation of weather data for 45 years archive and 1.5 years ahead forecast.</td></tr><tr><td><code>/overview</code></td><td><a href="https://openweathermap.org/api/one-call-3#weather_overview"><strong>Weather overview</strong></a></td><td>Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies.</td></tr></tbody></table>

> _Note:_ Data is available in JSON, XML, or HTML format



{% hint style="warning" %}
If you are using Dark Sky API, check our easy-to-follow[ migration process.](https://openweathermap.org/darksky-openweather-3)
{% endhint %}

#### _API Keys and Default API Calls_

**You can generate as many API keys as needed for your subscription.** We track the total usage from all of them.

**One Call API 3.0 sets a default limit of 2000 API calls per day**. If you need to change this limit, please check the information in the ["your account billing plans"](https://home.openweathermap.org/subscriptions) tab and update the standard settings. For more information, read our documentation page.

### Getting Started

#### _First Steps_

**To get started with the OpenWeather API** choose the [free plan to obtain current weather information](https://openweathermap.org/price). The free plan has a limit of 2000 calls a day.

**Subscribing to the free plan** **is** **a 2-step process** that goes as follows:

1. [Sign up](https://home.openweathermap.org/users/sign\_up) to OpenWeather to create your account.
2. Open the [Pricing](https://openweathermap.org/price).
3. Select Subscribe to the “Current Weather” free plan.

You will receive a "confirmation email” with further instructions to complete. After completing the instructions follow these steps:

1. [OpenWeather API key](https://home.openweathermap.org/api\_keys) page, provide a name for your API Key.
2. Select the desired type of data:&#x20;
   1. [Current and forecast weather data](https://openweathermap.org/api/one-call-3#current)
   2. [Weather data for timestamp](https://openweathermap.org/api/one-call-3#history)
   3. [Daily aggregation](https://openweathermap.org/api/one-call-3#history\_daily\_aggregation),
   4. [Weather overview](https://openweathermap.org/api/one-call-3#weather\_overview)

_Congratulations, you’re in and ready to start making_ API calls!

#### Making Your First API Call

**Request for Current Weather Forecast**

**A basic API call** **to get the current weather forecast** for a specific latitude and longitude (_latitude=33.44 and longitude =-94.04_ ), the API call will look as follows:

_`https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&appid={API key}`_

If you need to exclude some bits of information, add the exclude query parameter before the API key.

**Reading Your First API Response**

{% hint style="danger" %}
Parameters not showing in the API response indicate that the related weather phenomena just did not happen for the data of measurement provided.
{% endhint %}

**For the previous API call** the API response (in JSON format) will looks as follows:

API response (JSON):

```json
{

`  `"coord": {

`    `"lon": 10.99,

`    `"lat": 44.34

`  `},

`  `"weather": [

`    `{

`      `"id": 501,

`      `"main": "Rain",

`      `"description": "moderate rain",

`      `"icon": "10d"

`    `}

`  `],

`  `"base": "stations",

`  `"main": {

`    `"temp": 298.48,

`    `"feels\_like": 298.74,

`    `"temp\_min": 297.56,

`    `"temp\_max": 300.05,

`    `"pressure": 1015,

`    `"humidity": 64,

`    `"sea\_level": 1015,

`    `"grnd\_level": 933

`  `},

`  `"visibility": 10000,

`  `"wind": {

`    `"speed": 0.62,

`    `"deg": 349,

`    `"gust": 1.18

`  `},

`  `"rain": {

`    `"1h": 3.16

`  `},

`  `"clouds": {

`    `"all": 100

`  `},

`  `"dt": 1661870592,

`  `"sys": {

`    `"type": 2,

`    `"id": 2075663,

`    `"country": "IT",

`    `"sunrise": 1661834187,

`    `"sunset": 1661882248

`  `},

`  `"timezone": 7200,

`  `"id": 3163858,

`  `"name": "Zocca",

`  `"cod": 200

}    
```

#### _<mark style="color:orange;">(Coming soon!)</mark>_ <mark style="color:orange;"></mark><mark style="color:orange;">Authentication</mark>

**To get your credentials** to use the Open Weather API, you need to [sign up](https://home.openweathermap.org/users/sign\_up) to OpenWeather as explained in the \[First Steps]\(ADD LINK) section.

#### _<mark style="color:orange;">(Coming soon!)</mark>_ <mark style="color:orange;"></mark><mark style="color:orange;">Authorization</mark>

**After signing up,** you have to create an [**OpenWeather API key**](https://home.openweathermap.org/api\_keys) as explained in the \[First Steps]\(ADD LINK) section.

#### Status and Error Codes

_**Error Response Structure**_

Errors response payload returned for all types of errors has the following structure:

```json
{

`    `"cod":400,                          # Error code

`    `"message":"Invalid date format", # Error description

`    `"parameters": [                   # List of request parameters name related to the error

`        `"date"

`    `]

}  
```

_**Error Codes**_

Check the following table for more information about the status and error codes:

| Error Code | Description                                                                                                                                                                                                                                                                                                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **401**    | <p>Unauthorized. You can get 401 error if API token did not provided in the request or in case API token provided in the request does not grant access to this API.</p><p></p><p>You must add API token with granted access to the product to the request before returning it</p>                                                                                            |
| **404**    | <p>Not Found. You can get 404 error if data with requested parameters (lat, lon, date etc) does not exist in service database.</p><p></p><p>You must not retry the same request.</p>                                                                                                                                                                                         |
| **429**    | <p>Too Many Requests. You can get 429 error if the key quota of requests for the provided API to this API was exceeded.</p><p></p><p>You may retry the request after some time or after extending your key quota.</p>                                                                                                                                                        |
| **5xx**    | <p>Unexpected Error. You can get '5xx' error in case of other internal errors. Error Response code will be <code>5xx</code>.</p><p></p><p>Please contact us and enclose an example of your API request that receives this error in your email to let us analyse it and find a solution for you promptly.</p><p></p><p>You may retry the request which led to this error.</p> |

### Rate Limits and Thresholds

**The OpenWeather API’s** free plan has a limit of 2000 calls a day. If you need to increase the rate limit and thresholds, update the standard settings in the "Billing plans" tab in your Personal account.

### Best Practices

Check out the following table with the best practices that will enable you to get the most out of the OpenWeather API:

| Scope                             | Best Practice                                                                                                                                                                                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| API Key Management                | <p>Securely store your API key. Do not hardcode it in your application's source code, especially if the code is publicly accessible.</p><p></p><p>Use environment variables or secure app settings for API key management.</p>                   |
| Efficient Use of API Calls        | <p>To avoid reaching your API call limit, cache responses whenever possible, especially if you're requesting data that doesn't change frequently.</p><p></p><p>OpenWeather data updates every 10 minutes, so plan your requests accordingly.</p> |
| Use the Correct Endpoint          | <p>OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.).</p><p></p><p>Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p>             |
| Use the Correct Endpoint          | <p>:OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.).</p><p></p><p>Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p>            |
| Handle Errors Gracefully          | <p>Implement error handling in your application to manage API request failures or unexpected responses.</p><p></p><p>This includes handling HTTP status codes and parsing error messages returned by the API.</p>                                |
| Optimize Requests with Parameters | Use API request parameters effectively to get only the data you need. For example, you can exclude parts of the data you don't need with the exclude parameter in the One Call API 3.0.                                                          |
| Respect API Limits                | <p>Be aware of your subscription plan's API call limits and ensure your application does not exceed them. </p><p></p><p>Implement logic to throttle requests if necessary.</p>                                                                   |
| Use Units and Language Parameters | Customize API responses for your audience by using the units parameter to specify temperature and wind speed units, and the lang parameter to localize weather descriptions.                                                                     |
| Geocoding                         | Use the Geocoding API to convert between city names and geographical coordinates when necessary, as direct requests by city name may be deprecated for some endpoints.                                                                           |
| Subscription Management           | <p>Keep track of your subscription status and the features available to you. </p><p></p><p>Some features, like the One Call API 3.0, require a separate subscription.</p>                                                                        |
| Stay Updated                      | OpenWeather periodically updates its APIs and documentation. Stay informed about any changes that might affect your application by regularly checking the OpenWeather website or subscribing to their updates.                                   |

### Glossary

#### _**A**_

* **API Key:**\
  A unique identifier required to authenticate requests to the OpenWeather API. It's provided when you create an account on OpenWeather.
* **Accumulated Parameters**: \
  Data that represents the accumulation of weather elements, such as precipitation, over a specified period.
* **Air Pollution API**:\
  Provides data on air quality, including concentrations of pollutants like CO, NO2, and PM2.5, for any specified location.

#### _**B**_

* **Bulk Downloading**: \
  A feature that allows downloading large datasets of current weather or forecasts in JSON format, available for certain account types.

#### _**C**_

* **Callback Function**: \
  Used in JavaScript to handle asynchronous operations, such as receiving data from the API.
* **Climatic Forecast 30 Days**: \
  A long-term weather forecast that gives a general idea of the weather conditions for the coming month.
* **Current Weather Data**: \
  Real-time weather information for any location on Earth, including temperature, humidity, pressure, and more.

#### _**D**_

* **Daily Forecast 16 Days**: \
  A weather forecast service that provides daily weather data, including temperature and weather conditions, for up to 16 days ahead.

#### _**H**_

* **Hourly Forecast 4 Days**: \
  A detailed forecast that provides weather data in 3-hour intervals for up to 4 days ahead.
* **History API**: \
  Provides historical weather data for any location on Earth. Useful for analyzing past weather conditions.

#### _**F**_

* **5 Day / 3 Hour Forecast**: \
  A five-day weather forecast with details provided every three hours.
* **Fire Weather Index API**: \
  Offers information related to the risk of wildfire, which can be critical for fire prevention efforts in vulnerable areas.

#### _**G**_

* **Geocoding API**: Converts between addresses (like city names) and geographic coordinates (latitude and longitude), and vice versa.

#### _**J**_

* **JSON/XML Format**: \
  The formats in which API responses can be received. JSON is the default format, but XML is also available for most data types.

#### _**M**_

* **Multilingual Support**: \
  The API can return data in multiple languages, making it accessible to a global audience.

#### _**S**_

* **Statistical Weather Data API**: \
  Offers statistical data based on historical weather information, which can be used for research and analysis.

#### _**U**_

* **Units of Measurement**: \
  The API supports standard (Kelvin, meters/sec), metric (Celsius, meters/sec), and imperial (Fahrenheit, miles/hour) units for temperature, wind speed, and other measurements.

#### _**W**_

* **Weather Maps 2.0**: \
  A service that provides various weather maps, including forecast, historical, and current weather maps, which can be integrated into web and mobile applications.
