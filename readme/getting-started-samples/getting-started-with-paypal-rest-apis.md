# Getting Started with PayPal REST APIs

{% hint style="danger" %}
**Disclaimer**\
\
This is a portfolio sample.  <mark style="color:red;background-color:$danger;">Please keep in mind that</mark>**:**

* The sole purpose of this page is to showcase my understanding and practice of API documentation.&#x20;
* This content is not made from scratch. It is based on the publicely available[ official PayPal REST APIs documentation](https://developer.paypal.com/api/rest/).
* I focused on demonstrating a practical and user-friendly workflow on a best-effort basis.
* This is content is **intentionally incomplete** and _MUST NOT_ be used for production projects.
* If you need a comprehensive documentation, please check the available [official PayPal REST APIs documentation](https://developer.paypal.com/api/rest/).
{% endhint %}

## Overview <a href="#get-started-with-paypal-rest-apis" id="get-started-with-paypal-rest-apis"></a>

The PayPal APIs use **REST** and **OAuth 2.0 Access Tokens** for secure, standard integration, returning all data as JSON with clear HTTP response codes.&#x20;

You can test US integrations with a PayPal Developer account, or immediately explore, generate client code, and import our OpenAPI specs using Postman (check out our [Postman guide](https://developer.paypal.com/api/rest/postman)) without one.

Explore our REST API descriptions, generate code for your API clients, and import OpenAPI documents into compatible [third-party tools](https://tools.openapis.org/).

{% hint style="info" %}
**About Integrations**

You'll need a [PayPal Business account](https://www.paypal.com/business/open-business-account) to do the following: &#x20;

* Go live with integrations.
* Test integrations outside the US.
{% endhint %}

### Core Concepts

PayPal integrations use a **client ID** and **client secret** to authenticate API calls as described in the following table: &#x20;

| Cencept       | Description                                                                                                                                                                       |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Client ID     | A client ID identifies an app. You only need a client ID to get a PayPal payment button and standard credit and debit card fields.                                                |
| Client Secret | <p>A client secret authenticates a client ID. </p><p></p><p>To call PayPal APIs, you'll exchange your client ID and client secret for an access token. Keep this secret safe.</p> |
| Access Token  | An access token authenticates your app when calling PayPal REST APIs.                                                                                                             |



Before starting to use PayPal's REST APIs, you need to get your **client ID** and **client secret** as described in the following steps:&#x20;

1. [Sign up in PayPal](https://www.paypal.com/webapps/mpp/account-selection?intent=developer\&country.x=PT\&locale.x=en_US).&#x20;
2. Go to the [Dashboard](https://developer.paypal.com/dashboard/) and log in or sign up.
3. Select **Apps & Credentials**.
4. Select **Create App** to create a new project.\
   &#xNAN;_&#x4E;ote: New accounts come with a Default Application in the REST API apps section_.
5. Copy the **client ID** and **client secret** for your app.

### Getting Your Access Token

{% hint style="info" %}
**Prerequisites**

Curl installed.
{% endhint %}

After successfully getting your client ID and client secret, you can generate an [access token](getting-started-with-paypal-rest-apis.md#core-concepts) by completing the following steps:

1. Open a text/code editor.
2. Copy and paste the following code:

```
curl -v -X POST "https://api-m.sandbox.paypal.com/v1/oauth2/token" \ -u "CLIENT_ID:CLIENT_SECRET" \ -H "Content-Type: application/x-www-form-urlencoded" \ -d "grant_type=client_credentials"
```

3. Now modify the code by replacing:
   1. `CLIENT_ID` with your client ID.
   2. `CLIENT_SECRET` with your client secret.
4. Encode `CLIENT_ID:CLIENT_SECRET` in Base64 before sending it in the API call.
5. Run the updated code in your command line.

PayPal will return a response containing the access token and the number of seconds the access token is valid, as shown in the following JSON code:

```
{  "scope": "https://uri.paypal.com/services/invoicing https://uri.paypal.com/services/disputes/read-buyer https://uri.paypal.com/services/payments/realtimepayment https://uri.paypal.com/services/disputes/update-seller https://uri.paypal.com/services/payments/payment/authcapture openid https://uri.paypal.com/services/disputes/read-seller https://uri.paypal.com/services/payments/refund https://api-m.paypal.com/v1/vault/credit-card https://api-m.paypal.com/v1/payments/.* https://uri.paypal.com/payments/payouts https://api-m.paypal.com/v1/vault/credit-card/.* https://uri.paypal.com/services/subscriptions https://uri.paypal.com/services/applications/webhooks",  "access_token": "A21AAFEpH4PsADK7qSS7pSRsgzfENtu-Q1ysgEDVDESseMHBYXVJYE8ovjj68elIDy8nF26AwPhfXTIeWAZHSLIsQkSYz9ifg",  "token_type": "Bearer",  "app_id": "APP-80W284485P519543T",  "expires_in": 31668,  "nonce": "2020-04-03T15:35:36ZaYZlGvEkV4yVSz8g6bAKFoGSEzuy3CQcz3ljhibkOHg"}
```

{% hint style="info" %}
**Available languages**\
**You can call the PayPal OAuth API in any language.**
{% endhint %}

### Making API Calls

After successfuly getting an access token, you can start making API calls. Just replace `ACCESS-TOKEN` with your access token in the authorization header as follows:

&#x20;`-H Authorization: Bearer ACCESS-TOKEN`.&#x20;

When your access token expires, run again the previous curl code to request a new access token:

```
curl -v -X POST "https://api-m.sandbox.paypal.com/v1/oauth2/token" \ -u "CLIENT_ID:CLIENT_SECRET" \ -H "Content-Type: application/x-www-form-urlencoded" \ -d "grant_type=client_credentials"
```

### About PayPal Sandbox Account Credentials

The PayPal sandbox is a test environment that mirrors real-world transactions. By default, **PayPal developer accounts have 2 sandbox accounts:**&#x20;

* a personal account for buying
* a business account for selling.&#x20;

You'll get the login information for both accounts. Watch sandbox money move between accounts to test API calls.

To get sandbox login information for business and personal accounts complete the following steps:

1. Log into the [Developer Dashboard](https://developer.paypal.com/dashboard/).
2. Select **Testing Tools > Sandbox Accounts**.&#x20;
3. Locate the account you want to get credentials for and select ⋮.
4. Select **View/Edit Account** to see mock information such as the account email and system-generated password.
5. Sign in to [sandbox.paypal.com/signin](https://sandbox.paypal.com/signin) using your personal sandbox credentials.
6. In a separate browser, sign in with the business sandbox credentials.
7. Make API calls with your app's access token to see sandbox money move between personal and business accounts.

{% hint style="info" %}
**Additional sandobox accounts**\
You can create more sandbox accounts by selecting **Create account**.
{% endhint %}
