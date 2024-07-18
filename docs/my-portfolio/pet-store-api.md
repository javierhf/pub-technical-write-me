# Pet Store API

## Pet Store API Documentation Sample

### Overview

**The Pet Store API is a REST API that provides a comprehensive set of endpoints and functionalities** to manage your pet store business from pets, users and orders.

**The Pet Store API implements reusable data structure, request bodies and security schemes, and uses two types of authentication: OAuth2 and API Keys**. OAuth is used for operations requiring user-specific permissions, and API keys to secure other operations.

**Follow our comprehensive documentation to get the most** of the Pet Store API, and seamlessly integrate our pet store functionalities into your applications.

### API Endpoints

| Endpoint                 | Scope                                                       | Features                                                                                         |
| ------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `/pet`                   | All pets stored in your shop                                | By default, updates occur every 2 minutes                                                        |
| `/pet/findByStatus`      | Pets by status (_active_, _sold_, _reserved_, _incoming,_ ) | Allows combined statuses for example: _reserved_ and _incoming_                                  |
| `pet/{petId}`            | Get pet by ID                                               | `petId` format is customizable                                                                   |
| `/store/inventory`       | Get all pets in the store's inventory                       | By default, Inventory is sorted by status                                                        |
| `/store/order/`          | Get all orders of the store                                 | By default, last orders are shown first                                                          |
| `/store/order/{orderId}` | Get order by ID                                             | `orderId` format is customizable                                                                 |
| `/user`                  | Get all users of the store                                  | By default, users are updated every day (24 hours)                                               |
| `/user/login`            | Get all users currently logged in into the system           | By default, passwords are not shown. Access time is shown in the time zone of the current system |
| `/user/logout`           | Get all logged out users                                    | Access time is shown in the time zone of the current system                                      |
| `/user/{username}`       | Ger user information by user name                           | Case sensitive                                                                                   |

### Authentication and Authorization

| Method                     | Scope                                                     | Description                                                                                                                                                                                                                                                                                          |
| -------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OAuth2 (Implicit flow)** | <p><code>write:pets</code>\<br><code>read:pets</code></p> | <p>OAuth2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service.</p><p>The Pet Store API uses the implicit flow of OAuth2, which is suitable for public clients that cannot keep a secret (such as single-page applications).<br></p> |
| **API Key**                | _N/A_                                                     | <p>API Key authentication is a simple way of securing access by including a key in the request header.<br>This method is typically used for server-to-server communication.</p>                                                                                                                      |

The following table show the security requirements for each endpoint of the Pet Store API:

| Security Method               | Endpoint                                                                                                                                                                          | Scope                                                    |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **OAuth2 ('petstore\_auth')** | <p><code>/pet</code><br><code>/pet/findByStatus</code><br><code>/pet/findByTags</code><br><code>/pet/{petId}</code><br><code>/pet/{petId}</code><br><code>/store/order</code></p> | <p><code>write:pets</code><br><code>read:pets</code></p> |
| **API Key ('api\_key')**      | <p><code>/store/inventory</code><br><code>/pet/{petId}</code></p>                                                                                                                 |                                                          |

#### Implementing OAuth2 (Implicit Flow)

| **Authorization URL** | https://petstore3.swagger.io/oauth/authorize>                                                                                     |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Scopes**            | <p><code>write:pets</code>: Allows modification of pets in your account.<br><code>read:pets</code>: Allows reading your pets.</p> |

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

| **API Key parameters** | <p><strong><code>name: 'api_key'</code></strong><br><strong><code>location: 'header'</code></strong></p> |
| ---------------------- | -------------------------------------------------------------------------------------------------------- |

**To implement the API Key**  follows these steps:

1. **Get API Key:**\
   Get the API key from the API provider (usually through the API management portal).
2. **Include API key in your request:**\
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

### Status and Error Codes Handling

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
