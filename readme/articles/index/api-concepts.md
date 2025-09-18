# API Concepts

## What is an API?

API stands for Application Programming Interface, **a piece of code that allows communication and interaction (interface) between two systems** by defining available _resources_, interaction _methods_, _error codes_ and _how to handle them_, _authentication_ and _authorization_ means, and _data structures_ (schemas) for successful communication.

Communication between systems using an API is based in a **request-response architecture** with the following workflow:

1. System A sends a request to System B using one of the available API methods and providing the required data structures.
2. System B receives the request.
3. System B confirms the authentication and authorization credentials of System A.
4. System B confirms it can serve the request and returns:

> * a status code
> * the requested information in the defined data structure.

**If something fails**, System B returns the appropriate error code and message.

Therefore, a basic API flow diagram could look like this:

<figure><img src="../../../.gitbook/assets/mermaid-ai-diagram-2025-09-16-145630.png" alt=""><figcaption></figcaption></figure>

The **key discovery** **here** is the following:

> We'll be writing about the fundamental API concepts, covering how API resources, interaction methods, error codes (and how to handle them), authentication and authorization mechanisms, and data structures (schemas) relate and interact.
>
> These core API concepts directly inform and shape the structure of effective API documentation. Remember that API documentation have:
>
> 1. To enable users to get started quickly and implement further integrations.
> 2. To explain how to effectively and seamlessly use the API components—all within the boundaries defined by the API code and its specification file.
> 3. To help users understand our API thoroughly to allow customer's integrations.

This content will **prioritize the technical aspects of API usage**, rather than user-interface-based workflows like configuration guides, tutorials, or how-to articles.

{% hint style="info" %}
**Check the appendix**

Learn more in the [Appendix](appendix.md):

* [API Concepts](api-concepts.md#api-core-concepts)
* A [Lord of the Rings version](appendix.md) of the API flow diagram.
{% endhint %}

## Organizing our API

Now that we understand what an API is, let's explore how we organize and design them. **There are different approaches to design APIs**, for example _Code First_, _API Design-First_, and hybrid approaches. Each approach has its pros and cons and picking one over the other depends on our company or product developer team culture (or preferences).&#x20;

In any case, **technical writers have to follow-up the design process closely** (or prepare for a round of Subject-Matter Expert interviews) to increase the chances of a successful documentation with minimal rework.

From a technical writing perspective, the **API Design-First approach appears to be the most documentation-friendly** because it gives us the chance to:

* Familiarize ourselves with the API's business goals and context.
* Participate in all design stages.
* Access the API contract or specification from the beginning.
* Start the documentation process early on, allowing us to anticipate the documentation structure.

If you're new to API documentation or the first technical writer in your product development team, **insist in participating in all API design meetings and discussions**.

{% hint style="info" %}
**Check the Appendix**

Learn more about [API Design](api-concepts.md#api-design-approaches) approaches.
{% endhint %}

## API Specifications

An API specification file is a **human and machine-readable file that describes an API's features, functionality, requirements, and resources** (mostly in YAML or JSON) . The most common API specifications are:

* [OpenAPI](https://www.openapis.org/what-is-openapi) - Focused on resource management)
* [Arazzo](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) - Focused on user workflows.

The API specification file serves as **coding and documentation reference**, and even as a **contract among the parties** where we can find all the features, data schemas, and means of communication provided by the API.

Think of [**OpenAPI**](https://www.openapis.org/what-is-openapi) **and** [**Arazzo**](https://swagger.io/blog/the-arazzo-specification-a-deep-dive/) **specifications as storytellers**—they're lists of objects that tell our API's story, abut how our API supports our customers' success. Each object has its own set of mandatory and optional elements. These objects provide us, technical writers, with the **source material to create user-friendly and complete documentation**, both from scratch or using [Postman](https://learning.postman.com/)-like tools.

Remember: The more complete our API specification file is, our chances of crafting a complete and successful documentation increase.

{% hint style="info" %}
**Check the Appendix**

Learn more about [Open API and Arazzo specifications](api-concepts.md#openapi-and-arazzo-specifications).
{% endhint %}
