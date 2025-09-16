---
title: Understanding API Documentation
tags: draft
hidden: true
cover: ../../../.gitbook/assets/Gemini_Generated_Image_xd2ol0xd2ol0xd2o.png
coverY: 0
---

# Understanding API Documentation    

## Introduction  

As with any other technical documentation, API documentation tells a story, the story of our API and it does so in a very specific way. Following this line of thought, we could even state that API documentation is the most distinctive type of documentation within the software product's technical documentation universe. What makes API documentation that special? API documentation shares with users the intricacies of its design and features, supporting the story with technical information targeted to its favorite cohort: developers, testers, and engineers. Of course, there is a section called _Quick Start_ or _Getting Started_ that other roles could understand, but those three roles are the ones dealing with API implementation in depth.  

When we start learning about API documentation, we are often introduced to the two types of API docs: conceptual documentation and reference documentation. Conceptual documentation is intended to engage and enable users quickly, and reference documentation provides users with the comprehensive information needed to allow a deeper understanding. While this may help us understand the goal of each of these blocks of documentation and their constituent parts, it seems insufficient to understand and evaluate the current API documentation practices we can find online.  

In this article, I share with you my framework for understanding what an API is and how it relates to the different parts of any good API documentation. It took me a year of self-study and some money invested in online courses to develop this understanding. I hope you find it helpful.

## What is an API?

API stands for Application Programming Interface, a piece of code that acts as an interface between two systems by defining a set of available resources, the methods to interact with them in a request-response setup including error messages, authentication and authorization means of communication, and the data structures or schemas that ensure a successful communication.    

Here it is our first API-related vocabulary table:    

| API Vocabulary | Description |
| :--- | :--- |
| **Resources** | Paths on a server where the API stores and provides data. For example: `/users`, `/users/{id}`, and `/{id}/products`. Think of them as unique URLs for specific pieces of information. |
| **Method** | The action you want to perform on a resource, defined by an HTTP verb. The most common ones are:<ul><li>`GET` - To **read** a resource.</li><li>`POST` - To **create** a new resource.</li><li>`PUT` - To **completely replace** or update a resource.</li><li>`DELETE` - To **remove** a resource.</li><li>`PATCH` - To **partially update** a resource.</li></ul> |
| **Request** | A structured message sent by a client (System A) to a server (System B) using the API's rules. This message includes the desired **Method**, the **Resource** path, and sometimes data. An example is: `HTTP GET http://www.appdomain.com/users`. |
| **Response** | The structured answer a server (System B) sends back to a client (System A) after receiving a **Request**. It includes an HTTP **Status Code**, an optional message, and the requested data. The most common data formats are **JSON** and **XML**. |
| **Status Codes** and **Messages** | These are numeric codes and messages from the HTTP protocol that tell you the result of a **Request**. They're a simple way for the server to communicate whether a request was successful, failed, or needs more information. The codes are grouped into five categories: `1xx` (Informational), `2xx` (Success), `3xx` (Redirection), `4xx` (Client Errors), and `5xx` (Server Errors).  |
| **Authentication** | The process of verifying a user's or client's identity. It’s like showing your ID to prove you are who you say you are before you can access an API. |
| **Authorization** | The process of checking if an authenticated user or client has permission to access a specific resource or perform a certain action. This determines what you're allowed to do, even after your identity has been confirmed. |
| **Data Structure** or **Schema** | The blueprint or rules for organizing the data that is exchanged between the client and the server. It defines what fields are required, their data types, and how the information should be organized. The most popular formats for this are **JSON** and **XML**. |


## How Does an API Workflow Look Like?  

Imagine System A want to communicate with System B using an API. To do so, System A must send a request to System B using on of the available method of the API (described in the documentation!) and, if needed, provinding any required data in the structure that the API understand (also described in the documentation!). When System B receives the request, it will confirm that it can serve it back, for example, confirming that the required resource exists, and send back a status code of the operation and the information required (in case of a `GET`request) and as the data structure defined for the API. If something goes wrong, System B will send back the corresponding error code and message.  

Here is flow diagram of this workflow:  


```mermaid
graph TB
    subgraph "System A (Client)"
        A1[Application]
    end
    
    subgraph "API Layer"
        API[API Interface]
        
        subgraph "Resources/Endpoints"
            R1["/users"]
            R2["/orders"] 
            R3["/products"]
            R4["/inventory"]
        end
        
        subgraph "HTTP Methods"
            GET["GET<br/>(Read)"]
            POST["POST<br/>(Create)"]
            PUT["PUT<br/>(Update)"]
            DELETE["DELETE<br/>(Remove)"]
        end
        
        subgraph "Data Schema"
            JSON["JSON Format"]
            XML["XML Format"]
        end
    end
    
    subgraph "System B (Server)"
        B1[Database/Service]
    end
    
    A1 -->|1. Request| API
    API -->|2. Process Request| R1
    API --> R2
    API --> R3
    API --> R4
    
    R1 --> GET
    R1 --> POST
    R1 --> PUT
    R1 --> DELETE
    
    R2 --> GET
    R2 --> POST
    R2 --> PUT
    R2 --> DELETE
    
    GET --> JSON
    POST --> JSON
    PUT --> XML
    DELETE --> JSON
    
    API -->|3. Access Resource| B1
    B1 -->|4. Return Data| API
    API -->|5. Response| A1
    
    %% Minimalistic/Google-like colors
    %% Main nodes: subtle, clean background, dark text
    style A1 fill:#e8f0fe, stroke:#4285f4, stroke-width:2px, color:#3c4043
    style B1 fill:#e8f0fe, stroke:#4285f4, stroke-width:2px, color:#3c4043
    style API fill:#e8f0fe, stroke:#4285f4, stroke-width:2px, color:#3c4043

    %% Subgraphs: lighter background, same border as main nodes, dark text
    style Resources_Endpoints fill:#f0f5fd, stroke:#a0c3f7, stroke-width:1px, color:#3c4043
    style HTTP_Methods fill:#f0f5fd, stroke:#a0c3f7, stroke-width:1px, color:#3c4043
    style Data_Schema fill:#f0f5fd, stroke:#a0c3f7, stroke-width:1px, color:#3c4043

    %% Individual nodes within subgraphs: even lighter, almost white, with subtle border
    style R1 fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style R2 fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style R3 fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style R4 fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043

    style GET fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style POST fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style PUT fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style DELETE fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043

    style JSON fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043
    style XML fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043

    %% Link colors: subtle grey for general flow, bolder for main request/response
    linkStyle 0 stroke:#707070, stroke-width:2px;
    linkStyle 1 stroke:#a0a0a0;
    linkStyle 2 stroke:#a0a0a0;
    linkStyle 3 stroke:#a0a0a0;
    linkStyle 4 stroke:#a0a0a0;
    linkStyle 5 stroke:#a0a0a0;
    linkStyle 6 stroke:#a0a0a0;
    linkStyle 7 stroke:#a0a0a0;
    linkStyle 8 stroke:#a0a0a0;
    linkStyle 9 stroke:#a0a0a0;
    linkStyle 10 stroke:#a0a0a0;
    linkStyle 11 stroke:#a0a0a0;
    linkStyle 12 stroke:#a0a0a0;
    linkStyle 13 stroke:#a0a0a0;
    linkStyle 14 stroke:#a0a0a0;
    linkStyle 15 stroke:#a0a0a0;
    linkStyle 16 stroke:#a0a0a0;
    linkStyle 17 stroke:#707070, stroke-width:2px;
    linkStyle 18 stroke:#707070, stroke-width:2px;
    linkStyle 19 stroke:#707070, stroke-width:2px;
    linkStyle 20 stroke:#707070, stroke-width:2px;

    %% Subgraph styling to match
    classDef mainSubgraph fill:#e8f0fe, stroke:#4285f4, stroke-width:2px, color:#3c4043;
    classDef nestedSubgraph fill:#f0f5fd, stroke:#a0c3f7, stroke-width:1px, color:#3c4043;
    classDef nodeInSubgraph fill:#ffffff, stroke:#d1e2f9, stroke-width:1px, color:#3c4043;

    class A1 mainSubgraph;
    class API mainSubgraph;
    class B1 mainSubgraph;

    class R1,R2,R3,R4 nodeInSubgraph;
    class GET,POST,PUT,DELETE nodeInSubgraph;
    class JSON,XML nodeInSubgraph;

    %% Apply to subgraphs directly
    linkStyle 0 stroke:#4285f4,stroke-width:2px;
    linkStyle 1 stroke:#4285f4,stroke-width:1px;
    linkStyle 2 stroke:#4285f4,stroke-width:1px;
    linkStyle 3 stroke:#4285f4,stroke-width:1px;
    linkStyle 4 stroke:#4285f4,stroke-width:1px;
    linkStyle 17 stroke:#4285f4,stroke-width:1px;
    linkStyle 18 stroke:#4285f4,stroke-width:1px;
    linkStyle 19 stroke:#4285f4,stroke-width:2px;
    linkStyle 20 stroke:#4285f4,stroke-width:2px;

    style System_A_Client fill:#e8f0fe,stroke:#4285f4,stroke-width:2px,color:#3c4043
    style API_Layer fill:#e8f0fe,stroke:#4285f4,stroke-width:2px,color:#3c4043
    style Resources_Endpoints fill:#f0f5fd,stroke:#a0c3f7,stroke-width:1px,color:#3c4043
    style HTTP_Methods fill:#f0f5fd,stroke:#a0c3f7,stroke-width:1px,color:#3c4043
    style Data_Schema fill:#f0f5fd,stroke:#a0c3f7,stroke-width:1px,color:#3c4043
    style System_B_Server fill:#e8f0fe,stroke:#4285f4,stroke-width:2px,color:#3c4043
```  

If you prefer a Lord of the Rings like, here it is:    

## Organizing our API

We can design APIs in different ways, each with its pros and cons. From a technical writing perspective, the API Design-First approach appears to be the most documentation-friendly. This is because it gives us the chance to:

- Familiarize ourselves with the API's business goals and context.  
- Participate in all design stages.  
- Access the API contract or specification from the beginning.  
- Start the documentation process early on, allowing us to anticipate the documentation structure.

For informative purposes, in the following table, you'll find a description of the different API design approaches.

| API Coding Approach | Description | Pros | Cons |
| :------------------ | :---------- | :--- | :--- |
| **Code-First** | You start by writing your API's implementation code, then use tools or annotations within your code to generate the API specification (like OpenAPI/Swagger) automatically. The code is the source of truth. | - **Faster initial development:** You can jump straight into coding. \<br\> - **Always in sync:** The documentation is automatically updated with code changes. \<br\> - **Less overhead:** No need to manually maintain separate spec files. | - **Design can be an afterthought:** May lead to less consistent or well-thought-out API designs. \<br\> - **Tool dependency:** Relies heavily on code generation tools, which might have limitations. \<br\> - **Harder to get early feedback:** Design reviews can only happen after implementation starts. |
| **API Design-First** | You begin by designing and defining your API using an API specification language (like OpenAPI/Swagger, RAML, API Blueprint) before writing any code. Tools then generate boilerplate code or documentation from this specification. | - **Improved API consistency and quality:** Forces thoughtful design from the start. \<br\> - **Early feedback:** Stakeholders can review the API design before development begins. \<br\> - **Better developer experience:** Clear, well-documented APIs are easier to consume. \<br\> - **Parallel development:** Frontend and backend teams can work concurrently using the spec. | - **Slower initial setup:** Requires an extra design step before coding begins. \<br\> - **Syncing challenges:** If code deviates from the spec, manual updates are needed or a continuous integration process must be robust. \<br\> - **Requires design expertise:** Needs team members proficient in API design principles and specification languages. |
| **Hybrid Approach** | Combines elements of both Code-First and Design-First. You might start with a high-level design document or a rough spec, then implement the core API with Code-First tools, and finally refine the specification and code iteratively. | - **Balances speed and quality:** Get started quickly but still benefit from design principles. \<br\> - **Flexibility:** Can adapt to project needs and team strengths. \<br\> - **Iterative improvement:** Allows for continuous refinement of both code and documentation. | - **Complexity:** Can be harder to manage the workflow and keep everything synchronized. \<br\> - **Requires discipline:** Needs a clear process to ensure design and code remain aligned. \<br\> - **Potential for inconsistency:** If not managed well, you might end up with the drawbacks of both approaches. |  

## About API Specifications   

An API specification, or contract, is a human and machine-readable file (usually in YAML or JSON format) that thoroughly describes an API's features, functioning, requirements, and resources. The most common API specifications are [OpenAPI](https://www.openapis.org/what-is-openapi) (focused on resource management) and [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) (focused on user workflows).

[OpenAPI](https://www.openapis.org/what-is-openapi) and [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) specifications are built around objects (regardless of whether they are in YAML or JSON format), with each object having its own set of mandatory or optional constituent elements. These objects provide technical writers with the source material needed to create user-friendly and complete documentation.

Check the following table to learn more about the OpenAPI and Arazzo specifications:

| API Specification | Description | Best Use Cases |
| :---------------- | :---------- | :------------- |
| **OpenAPI Specification (OAS)** | A widely adopted, language-agnostic standard for **describing RESTful APIs**. It focuses on defining the API's surface: endpoints, operations, parameters, responses, and security schemes. It's essentially the blueprint for *what* an API does. | - **Defining API Contracts:** Creating a clear, machine-readable definition of a REST API. \<br\> - **Automated Tooling:** Generating documentation (Swagger UI), client SDKs, server stubs, and testing tools. \<br\g> - **Design-First Development:** Collaborating on API design before coding begins. \<br\> - **API Discovery & Consumption:** Helping developers understand and integrate with APIs quickly. |
| **Arazzo Specification** | A new specification focused on **describing API-level callbacks, webhooks, and asynchronous API interactions**. Unlike OpenAPI, which defines the initial request-response contract, Arazzo describes the *events and messages* that an API might send or receive asynchronously *after* an initial request, often involving a client-provided callback URL. It provides a formal way to define "reverse calls" or event-driven patterns in APIs. | - **Defining Webhooks:** Clearly specifying how an API will notify a client of events. \<br\> - **Asynchronous API Workflows:** Documenting long-running processes where the API calls back to the client upon completion or status change. \<br\> - **Event-Driven Architectures:** Formalizing the structure of events and callback messages. \<br\> - **Microservices Communication:** Detailing asynchronous inter-service communication patterns where one service triggers actions in another via callbacks. \<br\> - **Enhancing OpenAPI:** Arazzo is designed to complement OpenAPI, describing the asynchronous *behavior* of an API that OpenAPI defines the synchronous *interface* for. |

## So, What is API Documentation?

Now that we understand what an API is, how it works, its basic concepts, and the different approaches to API design, we can define API documentation as follows:

API documentation is a piece of documentation focused on a developer audience. It describes what the API is, its use cases, and all the resources and means of interaction available for two systems to communicate successfully. Geared towards a developer audience, API documentation must contain code examples to ensure user enablement and comprehensive content to facilitate system integration.

From this definition, it seems straightforward to distinguish between "hands-on documentation" and "reference documentation." These are commonly referred to as "Conceptual documentation" and "Reference documentation." Conceptual documentation briefly and effectively introduces our API (what it is, what it does, why it is useful) and encourages users to get started with it. Reference documentation, on the other hand, provides comprehensive information about the intricacies of our API (e.g., a list of resources, available methods, data schemas for both requests and responses, HTTP error codes and how to handle them, security topics, rate limiting, and code samples).

That being said, the following table shows the minimum sections to include in our API documentation: 
  
| Type of Documentation | Topics* |  
| -------------------- | --------- |  
| Conceptual documentation | <ol><li>Overview</li><li>Quick Start/Getting Started</li><li>How-Tos/Use-Case Tutorials</li><li>FAQ</li></ol>     |  
| Reference documentation |  <ol><li>Overview</li><li>Authentication and Authorization</li><li>Endpoints and Methods<ol><li>Request Parameters</li><li>Response Schema</li><li>Request/Response Examples (beyond just schema, actual JSON/XML bodies)</li></ol></li><li>Error Codes and Error Handling</li><li>Rate Limiting and Thresholds</li><li>Code Examples</li><li>Glossary</li><li>Best Practices</li><li>Changelog</li><li>SDKs/Libraries (if available, with links and usage info)</li><li>Environments (e.g., Sandbox, Production URLs)</li><li>Support/Contact Information</li></ol>      | 

ADD AN IMPORTATN NOTE FOR TOPICS: Remember that the list of topics for both conceptual documentation and reference documentation may (and should) change according to:  

* your APIS business goals and users context  
* ease of use


## Final Thoughts

We design an API because we find a space in the software universe to add value. For that value to be real, we have to support our users success by progressively disclosing all the information they need to try out our API quickly and to plan the integration with their systems with confidence and comfortable.
