---
title: Understanding API Documentation
tags: draft
hidden: true
cover: ../../../.gitbook/assets/Gemini_Generated_Image_xd2ol0xd2ol0xd2o.png
coverY: 0
---

# Understanding API Documentation

## Introduction

As with any other technical documentation, **API documentation tells a story, the story of our API** and it does so in a very specific way. API documentation is the most distinctive type of technical documentation in software products.

**What makes API documentation that special?** API documentation shares with users the intricacies of its design and features, supporting the story with technical information targeted to its favorite cohort: developers, testers, and engineers.

Of course, there is a section called _Quick Start_ or _Getting Started_ that other roles could understand, but those three roles are the ones dealing with API implementation in depth.

When we start learning about API documentation, we are often introduced to the two types of API docs: _conceptual documentation and reference documentation_. **Conceptual documentation** is intended to engage and enable users quickly, and **reference documentation** provides users with the comprehensive information needed to allow a deeper understanding.&#x20;

While this helps us understand each documentation type's goal, it's insufficient for evaluating current API documentation practices online.

In this article, I share with you my framework for understanding what an API is and how it relates to the different parts of any good API documentation. It took me a year of self-study and some money invested in online courses to develop this understanding. **I hope you find it helpful.**

## What is an API?

API stands for Application Programming Interface, **a piece of code that acts as an interface between two systems** by defining available resources, interaction methods, error handling, authentication/authorization, and data structures for successful communication.

Here it is our first **API-related vocabulary table**:

| API Vocabulary                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| --------------------------------- | -------------------------------------------------------------------------------------- |
| **Resources**                     | Paths on a server where the API stores and provides data. For example: `/users`, `/users/{id}`, and `/{id}/products`. Think of them as unique URLs for specific pieces of information.                                                                                                                                                                                                                                                                                                             |
| **Method**                        | <p>The action you want to perform on a resource, defined by an HTTP verb. The most common ones are:</p><ul><li><code>GET</code> - To <strong>read</strong> a resource.</li><li><code>POST</code> - To <strong>create</strong> a new resource.</li><li><code>PUT</code> - To <strong>completely replace</strong> or update a resource.</li><li><code>DELETE</code> - To <strong>remove</strong> a resource.</li><li><code>PATCH</code> - To <strong>partially update</strong> a resource.</li></ul> |
| **Request**                       | A structured message sent by a client (System A) to a server (System B) using the API's rules. This message includes the desired **Method**, the **Resource** path, and sometimes data. An example is: `HTTP GET http://www.appdomain.com/users`.                                                                                                                                                                                                                                                  |
| **Response**                      | The structured answer a server (System B) sends back to a client (System A) after receiving a **Request**. It includes an HTTP **Status Code**, an optional message, and the requested data. The most common data formats are **JSON** and **XML**.                                                                                                                                                                                                                                                |
| **Status Codes** and **Messages** | <p>These are numeric codes and messages from the HTTP protocol that tell you the result of a <strong>Request</strong>. They're a simple way for the server to communicate whether a request was successful, failed, or needs more information. </p><p></p><p>The codes are grouped into five categories: <code>1xx</code> (Informational), <code>2xx</code> (Success), <code>3xx</code> (Redirection), <code>4xx</code> (Client Errors), and <code>5xx</code> (Server Errors).</p>                 |
| **Authentication**                | The process of verifying a user's or client's identity. It's like showing your ID to prove you are who you say you are before you can access an API.                                                                                                                                                                                                                                                                                                                                               |
| **Authorization**                 | <p>The process of checking if an authenticated user or client has permission to access a specific resource or perform a certain action. </p><p></p><p>This determines what you're allowed to do, even after your identity has been confirmed.</p>                                                                                                                                                                                                                                                  |
| **Data Structure** or **Schema**  | <p>The blueprint or rules for organizing the data that is exchanged between the client and the server. It defines what fields are required, their data types, and how the information should be organized. </p><p></p><p>The most popular formats for this are <strong>JSON</strong> and <strong>XML</strong>.</p>                                                                                                                                                                                 |

## How Does an API Workflow Look Like?

When System A wants to communicate with System B using an API, it sends a request using available API methods and required data structures (both described in the documentation).

System B receives the request, confirms it can serve it (checking if resources exist), then returns a status code and requested information in the defined data structure. If something fails, it returns the appropriate error code and message.

Here is a basic API flow diagram of this workflow:&#x20;

<figure><img src="../../../.gitbook/assets/mermaid-ai-diagram-2025-09-16-145630.png" alt=""><figcaption></figcaption></figure>

If you prefer a **Lord of the Rings-like map**:

<figure><img src="../../../.gitbook/assets/Gemini_Generated_Image_v2zxgov2zxgov2zx.png" alt=""><figcaption></figcaption></figure>

## Organizing our API

**We can design APIs following different approaches**, each with its pros and cons. For informative purposes, in the following table, you'll find a description of the different API design approaches:

| API Coding Approach  | Description                                                                                                                                                                                                                             | Pros                                                                                                                                                                                                                                                                                                                                                                                                                                             | Cons                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------------------- | --------------------------------- | ------------------------------------ | ----------------------------------------------------------------------------------------------- |
| **Code-First**       | You start by writing your API's implementation code, then use tools or annotations within your code to generate the API specification (like OpenAPI/Swagger) automatically. The code is the source of truth.                            | <p>- <strong>Faster development:</strong> Jump straight into coding with auto-generated documentation.</p><p>- <strong>Always synchronized:</strong> Documentation updates automatically with code changes.</p>                                                                                                                                                                                                                                       | <p>- <strong>Design can be an afterthought:</strong> May lead to less consistent or well-thought-out API designs.</p><p>- <strong>Tool dependency:</strong> Relies heavily on code generation tools, which might have limitations.</p>                                                                                             |
| **API Design-First** | You begin by designing and defining your API using an API specification language (like OpenAPI/Swagger, RAML, API Blueprint) before writing any code. Tools then generate boilerplate code or documentation from this specification.    | <p>- <strong>Improved API quality:</strong> Forces thoughtful design from the start.</p><p>- <strong>Early feedback:</strong> Stakeholders can review the API design before development begins.</p><p>- <strong>Parallel development:</strong> Frontend and backend teams can work concurrently using the spec.</p> | <p>- <strong>Slower initial setup:</strong> Requires an extra design step before coding begins.</p><p>- <strong>Syncing challenges:</strong> If code deviates from the spec, manual updates are needed.</p>                |
| **Hybrid Approach**  | Combines elements of both Code-First and Design-First. You might start with a high-level design document or a rough spec, then implement the core API with Code-First tools, and finally refine the specification and code iteratively. | <p>- <strong>Balances speed and quality:</strong> Get started quickly but still benefit from design principles.</p><p>- <strong>Flexibility:</strong> Can adapt to project needs and team strengths.</p>                                                                                                                                      | <p>- <strong>Complexity:</strong> Can be harder to manage the workflow and keep everything synchronized.</p><p>- <strong>Requires discipline:</strong> Needs a clear process to ensure design and code remain aligned.</p>                                          |

From a technical writing perspective, the **API Design-First approach appears to be the most documentation-friendly** because it gives us the chance to:

* Familiarize ourselves with the API's business goals and context.
* Participate in all design stages.
* Access the API contract or specification from the beginning.
* Start the documentation process early on, allowing us to anticipate the documentation structure.

## About API Specifications

An API specification is a human and machine-readable file (YAML or JSON) that describes an API's features, functionality, requirements, and resources. The most common API specifications are [OpenAPI](https://www.openapis.org/what-is-openapi) (focused on resource management) and [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) (focused on user workflows).

[OpenAPI](https://www.openapis.org/what-is-openapi) and [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) specifications are built around objects (regardless of whether they are in YAML or JSON format), with each object having its own set of mandatory or optional constituent elements. These objects provide technical writers with the source material needed to create user-friendly and complete documentation.

Check the following table to learn more about the OpenAPI and Arazzo specifications:

| API Specification    | Description  | Best Use Cases    |
| -------------------- | ------------- | ----------------- |
| **OpenAPI Specification (OAS)** | A widely adopted, language-agnostic standard for **describing RESTful APIs**. It focuses on defining the API's surface: endpoints, operations, parameters, responses, and security schemes. It's essentially the blueprint for _what_ an API does.     | - **Defining API Contracts:** Creating a clear, machine-readable definition of a REST API. \<br> - **Automated Tooling:** Generating documentation (Swagger UI), client SDKs, server stubs, and testing tools. \<br\g> - **Design-First Development:** Collaborating on API design before coding begins. \<br> - **API Discovery & Consumption:** Helping developers understand and integrate with APIs quickly.  |
| **Arazzo Specification**        | A new specification focused on **describing API-level callbacks, webhooks, and asynchronous API interactions**. Unlike OpenAPI, which defines the initial request-response contract, Arazzo describes the _events and messages_ that an API might send or receive asynchronously _after_ an initial request, often involving a client-provided callback URL. It provides a formal way to define "reverse calls" or event-driven patterns in APIs. | - **Defining Webhooks:** Clearly specifying how an API will notify a client of events. \<br> - **Asynchronous API Workflows:** Documenting long-running processes where the API calls back to the client upon completion or status change. \<br> - **Event-Driven Architectures:** Formalizing the structure of events and callback messages. \<br> - **Microservices Communication:** Detailing asynchronous inter-service communication patterns where one service triggers actions in another via callbacks. \<br> - **Enhancing OpenAPI:** Arazzo is designed to complement OpenAPI, describing the asynchronous _behavior_ of an API that OpenAPI defines the synchronous _interface_ for. |

## So, What is API Documentation?

Now that we understand what an API is, how it works, its basic concepts, and the different approaches to API design, we can define API documentation as follows:

API documentation is a piece of documentation focused on a developer audience. It describes what the API is, its use cases, and all the resources and means of interaction available for two systems to communicate successfully. Geared towards a developer audience, API documentation must contain code examples to ensure user enablement and comprehensive content to facilitate system integration.

From this definition, it seems straightforward to distinguish between "hands-on documentation" and "reference documentation." These are commonly referred to as "Conceptual documentation" and "Reference documentation." Conceptual documentation briefly and effectively introduces our API (what it is, what it does, why it is useful) and encourages users to get started with it. Reference documentation, on the other hand, provides comprehensive information about the intricacies of our API (e.g., a list of resources, available methods, data schemas for both requests and responses, HTTP error codes and how to handle them, security topics, rate limiting, and code samples).

That being said, the following table shows the minimum sections to include in our API documentation:

| Type of Documentation    | Topics\*    |
| ------------------------ | ----------------------------------------------------------- |
| Conceptual documentation | <ol><li>Overview</li><li>Quick Start/Getting Started</li><li>How-Tos/Use-Case Tutorials</li><li>FAQ</li></ol>    |
| Reference documentation  | <ol><li>Overview</li><li>Authentication and Authorization</li><li><p>Endpoints and Methods</p><ol><li>Request Parameters</li><li>Response Schema</li><li>Request/Response Examples (beyond just schema, actual JSON/XML bodies)</li></ol></li><li>Error Codes and Error Handling</li><li>Rate Limiting and Thresholds</li><li>Code Examples</li><li>Glossary</li><li>Best Practices</li><li>Changelog</li><li>SDKs/Libraries (if available, with links and usage info)</li><li>Environments (e.g., Sandbox, Production URLs)</li><li>Support/Contact Information</li></ol> |

{% hint style="warning" %}
**Know your users and customize**
The previous list of topics represent a general representation of API documentation topics, but it is not written in stone. Customize it to satisfy your business and user need with the ultimate goal of engage and enable your users.
{% endhint %}

## Final Thoughts

We design APIs to add value in the software universe. To realize that value, we must support user success by progressively disclosing information they need to try our API quickly and integrate it confidently.