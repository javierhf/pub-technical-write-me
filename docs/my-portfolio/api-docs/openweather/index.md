---
title: My Technical Writer Portfolio  
status: new   

---   

# API Documentation Portfolio Samples

> **Disclaimer:**  
> _The one and only goal of this page is to apply my ideas and experience of technical writing to the Openweather - One CAll 3.0 API documentation to give readers the chance of comparing and start a fruitful conversation with learning purposes._  
> _No criticism intended_   
> **Tools**  
> _Markdown, GitHub, GitBook_  

## Original Content    

[One Call API 3.0](https://docs.openweather.co.uk/api/one-call-3)

## My Version  
### Reference Documentation  
**OpenWeather - One Call 3.0 API gets essential weather data, short-term and long-term forecasts and aggregated weather data** easily via our *One Call API 3.0*.  

**One Call API 3.0 is based on the proprietary [OpenWeather Model**](https://openweather.co.uk/technology)** and provide 4 endpoints which are updated every 10 minutes to get the most accurate and up-to-date weather data.
#### *OpenWeather One Call API 3.0 Endpoints*
**One Call API 3.0 contains 4 endpoints** and provides access to various data as shown in the following table:

|**Endpoint**|**Scope**|**Features**|
| :- | :- | :- |
|/onecall|<p>[**Current weather and forecasts:**](https://openweathermap.org/api/one-call-3#current)</p><p></p>|<p>- Minute forecast for 1 hour</p><p>&emsp;- Hourly forecast for 48 hours</p><p>&emsp;- Daily forecast for 8 days</p><p></p>|
|/timemachine|[**Weather data for any timestamp**](https://openweathermap.org/api/one-call-3#history)|45 years historical archive and 4 days ahead forecast|
|/day\_summary|[**Daily aggregation**](https://openweathermap.org/api/one-call-3#history_daily_aggregation)|Daily agreggation of weather data for 45 years archive and 1.5 years ahead forecast|
|/overview|[**Weather overview**](https://openweathermap.org/api/one-call-3#weather_overview)|Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies|

Data is available in JSON, XML, or HTML format

![Información con relleno sólido]*If your’re using Dark Sky API, check our [easy to follow migration process.* ](https://openweathermap.org/darksky-openweather-3)*

#### *API Keys and Default API Calls* 
**You can generate as many API keys as needed** for your subscription. We accumulate the total load from all of them.

**Regarding the number of API calls,** One call API 3.0 sets ups 2000 API calls per day by default for you. If you need to change this limit, please check the information in  ["your account billing plans" tab ](https://home.openweathermap.org/subscriptions) ando update standard settings. For more information m read our [](https://openweathermap.org/faq#onecall) page.
\*

#### Resources Description (Methods and Endpoints)
GET is the only HTTP method available for all resources. The root url for the API is <https://api.openweathermap.org/data/3.0/>opencall. 
##### */onecall*
![Advertencia con relleno sólido]Please note that One Call 3.0 is included in the "One Call by Call" subscription **only**. [Learn more](https://openweathermap.org/price).

Current and forecast data

**GET**   <https://api.openweathermap.org/data/3.0/onecall>
###### Parameters

|Name|Required|Description|
| :- | :- | :- |
|*lat*|Yes|Latitude, decimal (-90; 90). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*lon*|Yes|Longitude, decimal (-180; 180). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*appid*|Yes|Your unique API key (you can always find it on your account page under the "API key" tab)|
|*exclude*|No|<p>By using this parameter you can exclude some parts of the weather data from the API response. It should be a comma-delimited list (without spaces).</p><p>Available values:</p><p>- *current*</p><p>- *minutely*</p><p>- *hourly*</p><p>- *daily*</p><p>- *alerts*</p>|
|*units*|No|Units of measurement. *standard*, *metric* and *imperial* units are available. <br><br>If you do not use the *units* parameter, standard units will be applied by default. Learn more|
|*lang*|No|You can use the *lang* parameter to get the output in your language. Learn more|
###### Request Example
https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}
###### Response Example  

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

##### */timemachine*
![Advertencia con relleno sólido]Please note that One Call 3.0 is included in the "One Call by Call" subscription *only*. [Learn more](https://openweathermap.org/price).

Weather data for timestamp.

**GET**   <https://api.openweathermap.org/data/3.0/onecall/timemachine>
###### Parameters

|Name|Required|Description|
| :- | :- | :- |
|*lat*|Yes|Latitude, decimal (-90; 90). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*lon*|Yes|Longitude, decimal (-180; 180). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*appid*|Yes|Your unique API key (you can always find it on your account page under the "API key" tab)|
|*dt*|Yes|Timestamp (Unix time, UTC time zone), e.g. dt=1586468027. Data is available from January 1st, 1979 till 4 days ahead|
|*units*|No|Units of measurement. *standard*, *metric* and *imperial* units are available. <br><br>If you do not use the *units* parameter, standard units will be applied by default. Learn more|
|*lang*|No|You can use the *lang* parameter to get the output in your language. Learn more|

###### Request Example
https://api.openweathermap.org/data/3.0/onecall?lat=33.44&lon=-94.04&appid={API key}
###### Response Example  

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


##### */day\_summary*
![Advertencia con relleno sólido]Please note that One Call 3.0 is included in the "One Call by Call" subscription **only**. [Learn more](https://openweathermap.org/price).

Agreggated weather data for a particular date from 2<sup>nd</sup> January 1979 till long-term forecast for 1,5 years ahead.

**GET**   <https://api.openweathermap.org/data/3.0/onecall/day_summary>
###### Parameters

|Name|Required|Description|
| :- | :- | :- |
|*lat*|Yes|Latitude, decimal (-90; 90). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*lon*|Yes|Longitude, decimal (-180; 180). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*appid*|Yes|Your unique API key (you can always find it on your account page under the "API key" tab)|
|*datet*|Yes|Date in the `YYYY-MM-DD` format for which data is requested. Date is available for 45 years archive (starting from 1979-01-02) up to the 1,5 years ahead forecast to the current date|
|*units*|No|Units of measurement. *standard*, *metric* and *imperial* units are available. <br><br>If you do not use the *units* parameter, standard units will be applied by default. Learn more|
|*lang*|No|You can use the *lang* parameter to get the output in your language. Learn more|

###### Request Example
https://api.openweathermap.org/data/3.0/onecall/day\_summary?lat=39.099724&lon=-94.578331&date=2020-03-04&appid={API key}
###### Response Example  

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


##### */overview*
![Advertencia con relleno sólido]Please note that One Call 3.0 is included in the "One Call by Call" subscription **only**. [Learn more](https://openweathermap.org/price)

Weather overview information with a human-readable weather summary for today and tomorrow’s forecast, utilizing OpenWeather AI technologies.

**GET**   <https://api.openweathermap.org/data/3.0/onecall/overview>
###### Parameters

|Name|Required|Description|
| :- | :- | :- |
|*lat*|Yes|Latitude, decimal (-90; 90). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*lon*|Yes|Longitude, decimal (-180; 180). If you need the geocoder to automatic convert city names and zip-codes to geo coordinates and the other way around, please use our Geocoding API|
|*appid*|Yes|Your unique API key (you can always find it on your account page under the "API key" tab)|
|*datet*|No|The date the user wants to get a weather summary in the YYYY-MM-DD format. Data is available for today and tomorrow. If not specified, the current date will be used by default. <br><br>Please note that the date is determined by the timezone relevant to the coordinates specified in the API request|
|*units*|No|Units of measurement. *standard*, *metric* and *imperial* units are available. <br><br>If you do not use the *units* parameter, standard units will be applied by default. Learn more|
|*lang*|No|You can use the *lang* parameter to get the output in your language. Learn more|

###### Request Example
https://api.openweathermap.org/data/3.0/onecall/overview?lon=-11.8092&lat=51.509865&appid={API key}  

###### Response Example  

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
**OpenWeather - One Call 3.0 API gets essential weather data, short-term and long-term forecasts and aggregated weather data** easily via our *One Call API 3.0*.  

**One Call API 3.0 is based on the proprietary [OpenWeather Model**](https://openweather.co.uk/technology)** and provide 4 endpoints which are updated every 10 minutes to get the most accurate and up-to-date weather data.
#### *OpenWeather One Call API 3.0 Endpoints*
**One Call API 3.0 contains 4 endpoints** and provides access to various data as shown in the following table:

|**Endpoint**|**Scope**|**Features**|
| :- | :- | :- |
|/onecall|<p>[**Current weather and forecasts:**](https://openweathermap.org/api/one-call-3#current)</p><p></p>|<p>- Minute forecast for 1 hour</p><p>&emsp;- Hourly forecast for 48 hours</p><p>&emsp;- Daily forecast for 8 days</p><p></p>|
|/timemachine|[**Weather data for any timestamp**](https://openweathermap.org/api/one-call-3#history)|<p>45 years historical archive and 4 days ahead forecast</p><p></p>|
|/day\_summary|[**Daily aggregation**](https://openweathermap.org/api/one-call-3#history_daily_aggregation)|<p>Daily agreggation of weather data for 45 years archive and 1.5 years ahead forecast</p><p></p>|
|/overview|[**Weather overview**](https://openweathermap.org/api/one-call-3#weather_overview)|Weather overview with a human-readable weather summary for today and tomorrow's forecast, utilizing OpenWeather AI technologies|

Data is available in JSON, XML, or HTML format

![Información con relleno sólido]*if your’re using Dark Sky API, check our [easy to follow migration process.* ](https://openweathermap.org/darksky-openweather-3)*

*ADD SUBSCRIPTION PLANS*
#### *API Keys and Default API Calls* 
**You can generate as many API keys as needed** for your subscription. We accumulate the total load from all of them.

**Regarding the number of API calls,** One call API 3.0 sets ups 2000 API calls per day by default for you. If you need to change this limit, please check the information in  ["your account billing plans" tab ](https://home.openweathermap.org/subscriptions) ando update standard settings. For more information m read our [](https://openweathermap.org/faq#onecall) page.
### Getting Started
#### *First Steps*
**To get started with the OpenWeather API** choose the [free plan to obtain current weather information](https://openweathermap.org/price). The free plan has a limit of 2000 calls a day.

**Subscribing to the free plan** is a 2-step process that goes as folles: REVIEW

1. [Sign up](https://home.openweathermap.org/users/sign_up) to OpenWeather to create your account.
1. Open the [Princing](https://openweathermap.org/price).
1. Select Subscribe to the “Current Weather” free plan.
1. Follow the instruction in the “Confirmation Email” you will receive.
1. ` `[OpenWeather API key](https://home.openweathermap.org/api_keys) page, provide a name for your API Key.
1. Select the desired type of data: ?????
   1. [Current and forecasts weather data](https://openweathermap.org/api/one-call-3#current)
   1. [Weather data for timestamp](https://openweathermap.org/api/one-call-3#history)
   1. ` `[Daily aggregation](https://openweathermap.org/api/one-call-3#history_daily_aggregation),
   1. [Weather overview](https://openweathermap.org/api/one-call-3#weather_overview)

*Congratulations, you’re in and ready to start making* API calls!
#### *Making Your First API Call*
##### Request for Current Weather Forecast
**A basic API call** **to get the current weather forecast** for **a specific latitude and longitude (***latitude=33.44 and longitude =-94.04* **)**, the API call will look as follows: 

|<a name="_hlk167714924"></a><a name="_hlk167713619"></a>https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&appid={API key}|
| :- |

**If you need to exclude some bits of information**, add the exclude query parameter before the API key:

|https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&exclude=hourly,daily&appid={API key}|
| :- |

##### Reading Your First API Response
![Advertencia con relleno sólido]Parameters not showing in the API response indicate that the related weather phenomena just did not happen for the data of measurement provided. 

**For the previous API call:** https://api.openweathermap.org/data/2.5/weather?lat=33.44&lon=-94.04&appid={API key} the API response (in JSON format) will looks as follows:


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

#### Authentication
**To get your credentials** to use the Open Weather API, you need to [sign up](https://home.openweathermap.org/users/sign_up) to OpenWeather as explained in the [First Steps](ADD LINK) section.  

#### Authorization
**After signing up,** you have to create an **[OpenWeather API key](https://home.openweathermap.org/api_keys)** as explain in the [First Steps](ADD LINK) section.
#### (Status and )Error Codes
##### *Error Response Structure*
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
##### *Error Codes*
Check the following table for more information about the status and error codes:

|Error Code|Description|
| :- | :- |
|401|<p>Unauthorized. You can get 401 error if API token did not provided in the request or in case API token provided in the request does not grant access to this API. </p><p></p><p>You must add API token with granted access to the product to the request before returning it</p>|
|404|<p>Not Found. You can get 404 error if data with requested parameters (lat, lon, date etc) does not exist in service database. </p><p></p><p>You must not retry the same request.</p>|
|429|<p>Too Many Requests. You can get 429 error if key quota of requests for provided API to this API was exceeded. </p><p></p><p>You may retry request after some time or after extending your key quota.</p>|
|5xx|<p>Unexpected Error. You can get '5xx' error in case of other internal errors. Error Response code will be `5xx`.</p><p></p><p>Please contact us and enclose an example of your API request that receives this error into your email to let us analyze it and find a solution for you promptly. </p><p></p><p>You may retry the request which led to this error.</p>|

### Rate Limits( and Thresholds)
**The OpenWeather API’s** free plan has a limit of 2000 calls a day. If you need to increase the rate limit and thresholds, update the standard settings in the "Billing plans" tab in your Personal account.



### Best Practices
Check out the following table with the best practices that will enable you to get the most out of the OpenWeather API:

|SCOPE|BEST PRACTICE|
| :- | :- |
|API Key Management|<p>Securely store your API key. Do not hardcode it in your application's source code, especially if the code is publicly accessible. </p><p></p><p>Use environment variables or secure app settings for API key management.</p>|
|Efficient Use of API Calls|<p>To avoid reaching your API call limit, cache responses whenever possible, especially if you're requesting data that doesn't change frequently. </p><p>OpenWeather data updates every 10 minutes, so plan your requests accordingly.</p>|
|Use the Correct Endpoint|<p>OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.).</p><p></p><p>` `Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p>|
|Use the Correct Endpoint|<p>: OpenWeather offers various endpoints for different types of data (current weather, forecasts, historical data, etc.). </p><p></p><p>Use the specific endpoint that matches your data needs to ensure efficient use of the API.</p>|
|Handle Errors Gracefully|<p>Implement error handling in your application to manage API request failures or unexpected responses.</p><p></p><p>This includes handling HTTP status codes and parsing error messages returned by the API.</p>|
|Optimize Requests with Parameters|Use API request parameters effectively to get only the data you need. For example, you can exclude parts of the data you don't need with the exclude parameter in the One Call API 3.0.|
|Respect API Limits|Be aware of your subscription plan's API call limits and ensure your application does not exceed them. Implement logic to throttle requests if necessary.|
|Use Units and Language Parameters|Customize API responses for your audience by using the units parameter to specify temperature and wind speed units, and the lang parameter to localize weather descriptions.|
|Geocoding|Use the Geocoding API to convert between city names and geographical coordinates when necessary, as direct requests by city name may be deprecated for some endpoints.|
|Subscription Management|Keep track of your subscription status and the features available to you. Some features, like the One Call API 3.0, require a separate subscription.|
|Stay Updated|<p>OpenWeather periodically updates its APIs and documentation. Stay informed about any changes that might affect your application by regularly checking the OpenWeather website or subscribing to their updates.</p><p></p>|


### Glossary
#### ***A***
- **API Key**: A unique identifier required to authenticate requests to the OpenWeather API. It's provided when you create an account on OpenWeather.
- **Accumulated Parameters**: Data that represents the accumulation of weather elements, such as precipitation, over a specified period.
- **Air Pollution API**: Provides data on air quality, including concentrations of pollutants like CO, NO2, and PM2.5, for any specified location.
#### ***B***
- **Bulk Downloading**: A feature that allows downloading large datasets of current weather or forecasts in JSON format, available for certain account types.
#### ***C***
- **Callback Function**: Used in JavaScript to handle asynchronous operations, such as receiving data from the API.
- **Climatic Forecast 30 Days**: A long-term weather forecast that gives a general idea of the weather conditions for the coming month.
- **Current Weather Data**: Real-time weather information for any location on Earth, including temperature, humidity, pressure, and more.
#### ***D***
- **Daily Forecast 16 Days**: A weather forecast service that provides daily weather data, including temperature and weather conditions, for up to 16 days ahead.
#### ***H***
- **Hourly Forecast 4 Days**: A detailed forecast that provides weather data in 3-hour intervals for up to 4 days ahead.
- **History API**: Provides historical weather data for any location on Earth. Useful for analyzing past weather conditions.
#### ***F***
- **5 Day / 3 Hour Forecast**: A five-day weather forecast with details provided every three hours.
- **Fire Weather Index API**: Offers information related to the risk of wildfire, which can be critical for fire prevention efforts in vulnerable areas.
#### ***G***
- **Geocoding API**: Converts between addresses (like city names) and geographic coordinates (latitude and longitude), and vice versa.
#### ***J***
- **JSON/XML Format**: The formats in which API responses can be received. JSON is the default format, but XML is also available for most data types.
#### ***M***
- **Multilingual Support**: The API can return data in multiple languages, making it accessible to a global audience.
#### ***S***
- **Statistical Weather Data API**: Offers statistical data based on historical weather information, which can be used for research and analysis.
#### ***U***
- **Units of Measurement**: The API supports standard (Kelvin, meters/sec), metric (Celsius, meters/sec), and imperial (Fahrenheit, miles/hour) units for temperature, wind speed, and other measurements.
#### ***W***
- **Weather Maps 2.0**: A service that provides various weather maps, including forecast, historical, and current weather maps, which can be integrated into web and mobile applications.
