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

When we start learning about API documentation, we are often introduced to the two types of API docs: _conceptual documentation and reference documentation_. **Conceptual documentation** is intended to engage and enable users quickly, and **reference documentation** provides users with the comprehensive information needed to allow a deeper understanding.

While this helps us understand the goal of each API documentation type constituent parts, it seems to me insufficient for evaluating current API documentation practices online.

In this article, I share with you my understanding of how APIs relate to the different parts of its documentation to have a change of supporting our users' success. **I hope you find it helpful.**

## What is an API?

API stands for Application Programming Interface, **a piece of code that allows communication and interaction (interface) between two systems** by defining available resources, interaction methods, error handling, authentication and authorization, and data structures (schemas) for successful communication.

Here it is our first **API-related vocabulary table**:

| API Vocabulary                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Resources**                     | <p>Paths on a server where the API stores and provides data. For example: <code>/users</code>, <code>/users/{id}</code>, and <code>/{id}/products</code>. </p><p></p><p>Think of them as unique URLs for specific pieces of information.</p>                                                                                                                                                                                                                                                       |
| **Method**                        | <p>The action you want to perform on a resource, defined by an HTTP verb. The most common ones are:</p><ul><li><code>GET</code> - To <strong>read</strong> a resource.</li><li><code>POST</code> - To <strong>create</strong> a new resource.</li><li><code>PUT</code> - To <strong>completely replace</strong> or update a resource.</li><li><code>DELETE</code> - To <strong>remove</strong> a resource.</li><li><code>PATCH</code> - To <strong>partially update</strong> a resource.</li></ul> |
| **Request**                       | A structured message sent by a client (System A) to a server (System B) . This message includes the desired **Method**, the **Resource** path, and sometimes data. An example is: `HTTP GET http://www.appdomain.com/users`.                                                                                                                                                                                                                                                                       |
| **Response**                      | The structured answer a server (System B) sends back to a client (System A) after receiving a **Request**. It includes an HTTP **Status Code**, an optional message, and the requested data. The most common data formats are **JSON** and **XML**.                                                                                                                                                                                                                                                |
| **Status Codes** and **Messages** | <p>HTTP protocol numeric codes and messages that tell you the result of a <strong>Request</strong> whether a request was successful, failed, or needs more information.</p><p></p><p>The codes are grouped into five categories: <code>1xx</code> (Informational), <code>2xx</code> (Success), <code>3xx</code> (Redirection), <code>4xx</code> (Client Errors), and <code>5xx</code> (Server Errors).</p>                                                                                         |
| **Authentication**                | The process of verifying a user's or client's identity. It's like showing your ID to prove you are who you say you are before you can access an API.                                                                                                                                                                                                                                                                                                                                               |
| **Authorization**                 | The process of checking if an authenticated user or client has permission to access a specific resource or perform a certain action.                                                                                                                                                                                                                                                                                                                                                               |
| **Data Structure** or **Schema**  | <p>The blueprint or rules for organizing the data that is exchanged between the client and the server. It defines what fields are required, their data types, and how the information should be organized.</p><p></p><p>The most popular formats for this are <strong>JSON</strong> and <strong>XML</strong>.</p>                                                                                                                                                                                  |

## How Does an API Workflow Look Like?

When System A wants to communicate with System B using an API, it sends a request using available API methods and providing the required data structures (both described in the documentation) when required.

System B receives the request, confirms it can serve it . Then returns a status code and requested information in the defined data structure. If something fails, it returns the appropriate error code and message.

A basic API flow diagram could look like this:

<figure><img src="../../../.gitbook/assets/mermaid-ai-diagram-2025-09-16-145630.png" alt=""><figcaption></figcaption></figure>

If you prefer a **Lord of the Rings-like map**:

<figure><img src="../../../.gitbook/assets/Gemini_Generated_Image_v2zxgov2zxgov2zx.png" alt=""><figcaption></figcaption></figure>

## Organizing our API

**There are different approaches to design APIs**, each with its pros and cons.Picking one over the other depends on our company or product developer team culture (or preferences) or the API engineer one.  &#x20;

In the following table, you'll find an informative description of the different API design approaches:

| API Coding Approach  | Description                                                                                                                                                                                                                             | Pros                                                                                                                                                                                                                                                                                                                | Cons                                                                                                                                                                                                                                   |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Code-First**       | You start by writing your API's implementation code, then use tools or annotations within your code to generate the API specification (like OpenAPI/Swagger) automatically. The code is the source of truth.                            | <p>- <strong>Faster development:</strong> Jump straight into coding with auto-generated documentation.</p><p>- <strong>Always synchronized:</strong> Documentation updates automatically with code changes.</p>                                                                                                     | <p>- <strong>Design can be an afterthought:</strong> May lead to less consistent or well-thought-out API designs.</p><p>- <strong>Tool dependency:</strong> Relies heavily on code generation tools, which might have limitations.</p> |
| **API Design-First** | You begin by designing and defining your API using an API specification language (like OpenAPI/Swagger, RAML, API Blueprint) before writing any code. Tools then generate boilerplate code or documentation from this specification.    | <p>- <strong>Improved API quality:</strong> Forces thoughtful design from the start.</p><p>- <strong>Early feedback:</strong> Stakeholders can review the API design before development begins.</p><p>- <strong>Parallel development:</strong> Frontend and backend teams can work concurrently using the spec.</p> | <p>- <strong>Slower initial setup:</strong> Requires an extra design step before coding begins.</p><p>- <strong>Syncing challenges:</strong> If code deviates from the spec, manual updates are needed.</p>                            |
| **Hybrid Approach**  | Combines elements of both Code-First and Design-First. You might start with a high-level design document or a rough spec, then implement the core API with Code-First tools, and finally refine the specification and code iteratively. | <p>- <strong>Balances speed and quality:</strong> Get started quickly but still benefit from design principles.</p><p>- <strong>Flexibility:</strong> Can adapt to project needs and team strengths.</p>                                                                                                            | <p>- <strong>Complexity:</strong> Can be harder to manage the workflow and keep everything synchronized.</p><p>- <strong>Requires discipline:</strong> Needs a clear process to ensure design and code remain aligned.</p>             |

From a technical writing perspective, the **API Design-First approach appears to be the most documentation-friendly** because it gives us the chance to:

* Familiarize ourselves with the API's business goals and context.
* Participate in all design stages.
* Access the API contract or specification from the beginning.
* Start the documentation process early on, allowing us to anticipate the documentation structure.

## About API Specifications

An API specification is a **human and machine-readable file** (YAML or JSON) that describes an API's features, functionality, requirements, and resources. The most common API specifications are [OpenAPI](https://www.openapis.org/what-is-openapi) (focused on resource management) and [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) (focused on user workflows).

We could explain [**OpenAPI**](https://www.openapis.org/what-is-openapi) **and** [**Arazzo**](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) **specifications files as an objects's story** (regardless of whether they are in YAML or JSON format), with _each object having its own set of mandatory and optional constituent elements_.  The following piece of an incomplete OpenAPI specification file shows some of those objects: &#x20;

```yaml
openapi: 3.0.4
info:
  title: Swagger Petstore - OpenAPI 3.0
  description: |-
    This is a sample Pet Store Server based on the OpenAPI 3.0 specification.  You can find out more about
    Swagger at [https://swagger.io](https://swagger.io). In the third iteration of the pet store, we've switched to the design first approach!
    You can now help us improve the API whether it's by making changes to the definition itself or to the code.
    That way, with time, we can improve the API in general, and expose some of the new features in OAS3.

    Some useful links:
    - [The Pet Store repository](https://github.com/swagger-api/swagger-petstore)
    - [The source API definition for the Pet Store](https://github.com/swagger-api/swagger-petstore/blob/master/src/main/resources/openapi.yaml)
  termsOfService: https://swagger.io/terms/
  contact:
    email: apiteam@swagger.io
  license:
    name: Apache 2.0
    url: https://www.ap
externalDocs:
servers:
tags:
  /pet:
    put:
      tags:
        - pet
      summary: Update an existing pet.
      description: Update an existing pet by Id.
      operationId: updatePet
      requestBody:
        description: Update an existent pet in the store
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Pet'
          application/xml:
            schema:
              $ref: '#/components/schemas/Pet'
          application/x-www-form-urlencoded:
            schema:
              $ref: '#/components/schemas/Pet'
        required: true
      responses:
        '200':
          description: Successful operation
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Pet'
            application/xml:
              schema:
                $ref: '#/components/schemas/Pet'
        '400':
          description: Invalid ID supplied
        '404':
          description: Pet not found
        '422':
          description: Validation exception
        default:
          description: Unexpected error
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
      security:
        - petstore_auth:
            - write:pets
            - read:pets
paths:
components:
```

These objects provide technical writers with the source material needed to create user-friendly and complete documentation, both from scratch or using[ Postman](https://learning.postman.com/)-like tools.

Check the following table to learn more about the OpenAPI and Arazzo specifications:

| API Specification               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                       | Best Use Cases                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OpenAPI Specification (OAS)** | A widely adopted, language-agnostic standard for **describing RESTful APIs**. It focuses on defining the API's surface: endpoints, operations, parameters, responses, and security schemes. It's essentially the blueprint for _what_ an API does.                                                                                                                                                                                                | <p>- <strong>Defining API Contracts:</strong> Creating a clear, machine-readable definition of a REST API.</p><p>- <strong>Automated Tooling:</strong> Generating documentation (Swagger UI), client SDKs, server stubs, and testing tools.</p><p>- <strong>Design-First Development:</strong> Collaborating on API design before coding begins.</p><p> - <strong>API Discovery &#x26; Consumption:</strong> Helping developers understand and integrate with APIs quickly.</p>                                                                                                                                                                                                                                                                                                           |
| **Arazzo Specification**        | A new specification focused on **describing API-level callbacks, webhooks, and asynchronous API interactions**. Unlike OpenAPI, which defines the initial request-response contract, Arazzo describes the _events and messages_ that an API might send or receive asynchronously _after_ an initial request, often involving a client-provided callback URL. It provides a formal way to define "reverse calls" or event-driven patterns in APIs. | <p>- <strong>Defining Webhooks:</strong> Clearly specifying how an API will notify a client of events. </p><p>- <strong>Asynchronous API Workflows:</strong> Documenting long-running processes where the API calls back to the client upon completion or status change. </p><p>- <strong>Event-Driven Architectures:</strong> Formalizing the structure of events and callback messages. </p><p>- <strong>Microservices Communication:</strong> Detailing asynchronous inter-service communication patterns where one service triggers actions in another via callbacks. </p><p>- <strong>Enhancing OpenAPI:</strong> Arazzo is designed to complement OpenAPI, describing the asynchronous <em>behavior</em> of an API that OpenAPI defines the synchronous <em>interface</em> for.</p> |

## So, What is API Documentation?

Now that we understand what an API is, how it works, its basic concepts, and the different approaches to API design, we could define API documentation as follows:

> API documentation is a piece of documentation focused on a developer audience. It describes what the API is, all the resources and means of interaction available for two systems to communicate successfully while providing working code examples to ensure user enablement. It must include working code examples that allow developers to quickly test and understand the API's functionality, and comprehensive reference content for deeper system integration.

From this definition, it seems straightforward to distinguish between "hands-on documentation" (commonly referred as "Conceptual documentation") and "reference documentation" (commonly refferred as... well "Reference documentation").&#x20;

On the one hand, **Conceptual documentation** briefly and effectively introduces our API: what it is, what it does, why it is useful, and how to get started quickly. **Reference documentation**, on the other hand, provides comprehensive information about the intricacies of our API (e.g., a list of all the resources, available methods, data schemas for both requests and responses, HTTP error codes and how to handle them, security topics, rate limiting, and code samples).

This being said, an API documentation should cover, at least, the following topics:

| Type of Documentation    | Topics\*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Conceptual documentation | <ol><li>Overview</li><li>Quick Start/Getting Started</li><li>How-Tos/Use-Case Tutorials</li><li>FAQ</li></ol>                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Reference documentation  | <ol><li>Overview</li><li>Authentication and Authorization</li><li><p>Endpoints and Methods</p><ol><li>Request Parameters</li><li>Response Schema</li><li>Request/Response Examples (beyond just schema, actual JSON/XML bodies)</li></ol></li><li>Error Codes and Error Handling</li><li>Rate Limiting and Thresholds</li><li>Code Examples</li><li>Glossary</li><li>Best Practices</li><li>Changelog</li><li>SDKs/Libraries (if available, with links and usage info)</li><li>Environments (e.g., Sandbox, Production URLs)</li><li>Support/Contact Information</li></ol> |
|                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### Know Your Audience and Customize

Now that you know the minimum topics to cover with your API documentation, remember the core principle of technical writing: **Know you audience**. &#x20;

The previous list of topics represented the main topics to cover in your API documentation topics, but it is not a rule written in stone. If your business and customer goals or needs require more topics or merging different topics, do it (and test it!).&#x20;

For example, if you customer or support department points out an increasing demand from customer to have specific API workflows documented, go for it and include them in your tutorials' section. Or, intead of having different topics for _Endpoint and Methods_ and _Code Examples,_ evaluate if merging them would be more practical for your users, or even having _Endpoint and Methods, Error Coides and Error Handling_ merged with _Code Examples._

## Final Thoughts

### Final Thoughts

Making sense of what we are learning helps us to go further, to take the next step. If API and API documentation seem like a complicated topic, think of it as a story you write to enable your users to understand it—in a hands-on approach.

