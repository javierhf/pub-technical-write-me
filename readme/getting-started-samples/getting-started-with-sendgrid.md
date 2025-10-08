# Getting Started with Sendgrid

{% hint style="danger" %}
**Disclaimer**\
\
This is a portfolio sample.  <mark style="color:red;background-color:$danger;">Please keep in mind that</mark>**:**

* The sole purpose of this page is to showcase my understanding and practice of API documentation.&#x20;
* This content is not made from scratch. It is based on the publicely available[ official Sendgrid API documentation](https://www.twilio.com/docs/sendgrid/for-developers/sending-email/api-getting-started).
* I focused on demonstrating a practical and user-friendly workflow on a best-effort basis.
* This is content is intentionally incomplemt and _MUST NOT_ be used for production projects.
* If you need a comprehensive documentation, please check the available[ official Sendgrid API documentation](https://www.twilio.com/docs/sendgrid/for-developers/sending-email/api-getting-started).
{% endhint %}

## Overview

There are several ways you can get started with the SendGrid API. The following instructions describe how to send your first email using cURL calls. This is one of many ways to send email with the SendGrid API - we also have implementations for the following libraries:

* [PHP](https://github.com/sendgrid/sendgrid-php)
* [Python](https://github.com/sendgrid/sendgrid-python)
* [Node.js](https://github.com/sendgrid/sendgrid-nodejs)
* [Java](https://github.com/sendgrid/sendgrid-java)
* [C#](https://github.com/sendgrid/sendgrid-csharp), [Go](https://github.com/sendgrid/sendgrid-go)
* [Ruby](https://github.com/sendgrid/sendgrid-ruby)

## First Steps

Before you can start using the API, complete the following steps:

1. Create a SendGrid [account](https://sendgrid.com/pricing/).
2. Obtain your [API Key](https://app.sendgrid.com/settings/api_keys).

## Building Your API Call

{% hint style="info" %}
**Prerequisites**

* [Curl](https://curl.haxx.se/) installed on your machine.
* [Sender Authentication](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication) set up in your account.
* Active API key. Basic Authentication is no longer accepted.
{% endhint %}

A Sendgrid API call consists of **a host**, **an authentication header**, and **a request**. When building your API call remember that:

* The host for Web API v3 requests is always `https://api.sendgrid.com/v3/`.
* The[ Authorization header](https://www.twilio.com/docs/sendgrid/api-reference/how-to-use-the-sendgrid-v3-api/authentication#authorization-header) must include an [API Key](https://app.sendgrid.com/settings/api_keys).
* Submit your payload to a resource using JSON format for `POST` and `PUT` requests.
* Total message size (message, headers, and attachments) must not exceed 20MB. &#x20;
* Do not use IP addresses. Set your server host to `https://api.sendgrid.com/v3/` instead to avoid unexpected interruptions due to a change in the SendGrid IPs.

## Sending an Email Using the API

To send an email using the SendGrid API follow these steps:

1. Copy and paste the following curl code in a text editor:

```bash
curl --request POST \
--url https://api.sendgrid.com/v3/mail/send \
--header 'Authorization: Bearer <<YOUR_API_KEY>>' \
--header 'Content-Type: application/json' \
--data '{"personalizations":[{"to":[{"email":"john.doe@example.com","name":"John Doe"}],"subject":"Hello, World!"}],"content": [{"type": "text/plain", "value": "Heya!"}],"from":{"email":"sam.smith@example.com","name":"Sam Smith"},"reply_to":{"email":"sam.smith@example.com","name":"Sam Smith"}}'
```

3. Replace `<<YOUR_API_KEY>>` with your [API key](getting-started-with-sendgrid.md#first-steps)
4.  In the `--data` parameter, add your specific information in the following keys:

    > `"to"`\
    > `"from"`\
    > `"reply_to"`\
    > `"name"`\
    > `"subject"`
5. Copy the code and paste it in your terminal.
6. Hit **Enter**.
7. Check the inbox of the address you specified as the \`"to" email address and see your message.
