# Pet Store API

## Pet Store API Documentation



{% hint style="warning" %}
**Disclaimer**\
This page is _NOT_ the official documentation of Swagger's Pet Store API. The sole purpose of this page is to showcase my technical writing skills by applying my ideas and experience to Swagger's Pet Store API.
{% endhint %}

### Overview

**The Pet Store API is a REST API that provides a comprehensive set of endpoints and functionalities** to manage your pet store business from pets, users, and orders.

**The Pet Store API implements reusable data structure, request bodies, and security schemes, and uses two types of authentication: OAuth2 and API Keys**. OAuth is used for operations requiring user-specific permissions, and API keys to secure other operations.

**To work the Pet Store API,** we have designed the following endpoints:



<table><thead><tr><th width="278">Endpoint</th><th>Scope</th><th>Features</th></tr></thead><tbody><tr><td><code>/pet</code></td><td>All pets stored in your shop</td><td>By default, updates occur every 2 minutes</td></tr><tr><td><code>/pet/findByStatus</code></td><td>Pets by status (<em>active</em>, <em>sold</em>, <em>reserved</em>, <em>incoming,</em> )</td><td>Allows combined statuses for example: <em>reserved</em> and <em>incoming</em></td></tr><tr><td><code>pet/{petId}</code></td><td>Get pet by ID</td><td><code>petId</code> format is customizable</td></tr><tr><td><code>/store/inventory</code></td><td>Get all pets in the store's inventory</td><td>By default, Inventory is sorted by status</td></tr><tr><td><code>/store/order/</code></td><td>Get all orders of the store</td><td>By default, last orders are shown first</td></tr><tr><td><code>/store/order/{orderId}</code></td><td>Get order by ID</td><td><code>orderId</code> format is customizable</td></tr><tr><td><code>/user</code></td><td>Get all users of the store</td><td>By default, users are updated every day (24 hours)</td></tr><tr><td><code>/user/login</code></td><td>Get all users currently logged in into the system</td><td>By default, passwords are not shown. Access time is shown in the time zone of the current system</td></tr><tr><td><code>/user/logout</code></td><td>Get all logged out users</td><td>Access time is shown in the time zone of the current system</td></tr><tr><td><code>/user/{username}</code></td><td>Ger user information by user name</td><td>Case sensitive</td></tr></tbody></table>

### Security Fundamentals

**Regarding authentication and authorization**, the Pet Store API uses the methods described in the following table:

| Method                     | Scope                                                     | Description                                                                                                                                                                                                                                                                                                 |
| -------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OAuth2 (Implicit flow)** | <p><code>write:pets</code>\<br><code>read:pets</code></p> | <p>OAuth2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service.</p><p></p><p>The Pet Store API uses the implicit flow of OAuth2, which is suitable for public clients that cannot keep a secret (such as single-page applications).<br></p> |
| **API Key**                | _N/A_                                                     | <p>API Key authentication is a simple way of securing access by including a key in the request header.</p><p><br>This method is typically used for server-to-server communication.</p>                                                                                                                      |

**Each endpoint has a scope depending on the security method,** as shown in the following table:

| Security Method               | Endpoint                                                                                                                                                                          | Scope                                                    |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **OAuth2 ('petstore\_auth')** | <p><code>/pet</code><br><code>/pet/findByStatus</code><br><code>/pet/findByTags</code><br><code>/pet/{petId}</code><br><code>/pet/{petId}</code><br><code>/store/order</code></p> | <p><code>write:pets</code><br><code>read:pets</code></p> |
| **API Key ('api\_key')**      | <p><code>/store/inventory</code><br><code>/pet/{petId}</code></p>                                                                                                                 |                                                          |

### Implementing OAuth2 (Implicit Flow)

<table><thead><tr><th width="238">Topic</th><th>Information</th></tr></thead><tbody><tr><td><strong>Authorization URL</strong></td><td>https://petstore3.swagger.io/oauth/authorize></td></tr><tr><td><strong>Scopes</strong></td><td><code>write:pets</code>: Allows modification of pets in your account.<br><code>read:pets</code>: Allows reading your pets.</td></tr></tbody></table>

**To implement OAuth2 (Implicit flow)** you have to _request authorization,_ _receive the access token,_ and _use the access token as_ follows:

1. **Request authorization:**\
   Redirect the user to the authorization URL with the required parameters (client ID, redirect URI, response type, and scope), for example:  `https://petstore3.swagger.io/oauth/authorize?client_id=<YOUR_CLIENT_ID>&redirect_uri==<YOUR_REDIRECT_URI>&response_type=token&scope=write:pets read:pets`
2. **Receive access token:**
   1. After the user grants permission, they are redirected back to your application with the access token in the URL fragment
   2. Extract the access token from the URL
3.  **Use access token:**\
    Include the access token in the ‘Authorization’ header for API requests, for example:\
    `GET /pet HTTP/1.1`

    `Host: petstore3.swagger.io`

    `Authorization: Bearer ACCESS_TOKEN`



### Implementing API Key

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>API Key parameters</strong></td><td></td></tr><tr><td><strong><code>name: 'api_key'</code></strong><br><strong><code>location: 'header'</code></strong></td><td></td></tr></tbody></table>

**To implement the API Key** follow these steps:

1. **Get the API Key:**\
   Get the API key from the API provider (usually through the API management portal).
2. **Include the API key in your request:**\
   Add the API key to the request header, for example:\
   `GET /pet/{petId} HTTP/1.1`\
   `Host: petstore3.swagger.io`\
   `api_key: YOUR_API_KEY`    \


### _<mark style="color:orange;">(Coming soon!) Resources: Endpoints and Methods</mark>_

`/endpoint`

_Method_ Method description

Sample Request

Sample/Response Definitions Schema

### _<mark style="color:orange;">(Coming soon!)</mark>_ _<mark style="color:orange;">Request Parameters</mark>_

### _<mark style="color:orange;">(Coming soon!) Response Schema</mark>_

### _<mark style="color:yellow;">(Complete information!)</mark>_ <mark style="color:yellow;">Status and Error Codes Handling</mark>

#### `/pet`

**PUT**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Pet not found        | _N/A_                |
| **'422'**   | Validation exception | _TO DO_              |

**POST**

| Status Code | Description          | Solution                      |
| ----------- | -------------------- | ----------------------------- |
| **'200'**   | Successful operation | _N/A_                         |
| **'400'**   | Invalid input        | _Review your input structure_ |
| **'422'**   | Validation exception | _TO DO_                       |

#### `/pet/findByStatus`

**GET**

| Status Code | Description          | Solution                       |
| ----------- | -------------------- | ------------------------------ |
| **'200'**   | Successful operation | _N/A_                          |
| **'400'**   | Invalid status value | _Provide a valid status value_ |

#### /`pet/{petId}`

**GET**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Pet not found        | _N/A_                |

**POST**

| Status Code | Description         | Solution             |
| ----------- | ------------------- | -------------------- |
| **'400'**   | Invalid ID supplied | _Provide a valid ID_ |

**DELETE**

| **Status Code** | **Description**   | **Solution**         |
| --------------- | ----------------- | -------------------- |
| **'400'**       | Invalid pet value | _Provide a valid ID_ |

#### /`store/order/{orderId}`

**GET**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Order not found      | _N/A_                |

**DELETE**



| Status Code | Description         | Solution           |
| ----------- | ------------------- | ------------------ |
| '400'       | Invalid ID supplied | Provide a valid ID |
| '404'       | Order nor found     | N/A                |

#### `/pet`

**PUT**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Pet not found        | _N/A_                |
| **'422'**   | Validation exception | _TO DO_              |

**POST**

| Status Code | Description          | Solution                      |
| ----------- | -------------------- | ----------------------------- |
| **'200'**   | Successful operation | _N/A_                         |
| **'400'**   | Invalid input        | _Review your input structure_ |
| **'422'**   | Validation exception | _TO DO_                       |

#### `/pet/findByStatus`

**GET**

| Status Code | Description          | Solution                       |
| ----------- | -------------------- | ------------------------------ |
| **'200'**   | Successful operation | _N/A_                          |
| **'400'**   | Invalid status value | _Provide a valid status value_ |

#### `/pet/{petId}`

**GET**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Pet not found        | _N/A_                |

**POST**

| Status Code | Description         | Solution             |
| ----------- | ------------------- | -------------------- |
| **'400'**   | Invalid ID supplied | _Provide a valid ID_ |

**DELETE**

| Status Code | Description       | Solution             |
| ----------- | ----------------- | -------------------- |
| **'400'**   | Invalid pet value | _Provide a valid ID_ |

#### `/store/order/{orderId}`

**GET**

| Status Code | Description          | Solution             |
| ----------- | -------------------- | -------------------- |
| **'200'**   | Successful operation | _N/A_                |
| **'400'**   | Invalid ID supplied  | _Provide a valid ID_ |
| **'404'**   | Order not found      | _N/A_                |

**DELETE**

| Status Code | Description         | Solution             |
| ----------- | ------------------- | -------------------- |
| **'400'**   | Invalid ID supplied | _Provide a valid ID_ |
| **'404'**   | Order not found     | _N/A_                |
