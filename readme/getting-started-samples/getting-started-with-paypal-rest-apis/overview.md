# Overview

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
