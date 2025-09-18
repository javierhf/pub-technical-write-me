# From Concepts to Docs

## So, What is API Documentation?

So far we have learned about _what an API_ is, _how it works_, its _basic concepts_, and the different _API design approaches_ and _API specifications_. To connect all the dots, we could define API documentation as follows:

> API documentation is a piece of documentation focused on a developer audience. It describes what the API is, all the resources and means of interaction available for two systems to communicate successfully while providing working code examples to ensure user enablement. It also must include comprehensive reference content to support deeper system integration.

From this definition, it seems straightforward to distinguish between **"hands-on documentation"** (traditionally referred as "Conceptual documentation") and **"reference documentation"** (commonly referred as... well "Reference documentation").

On the one hand, what we called **Hands-on documentation** introduces our API to our users:

* What it is the API
* What it does
* Why it is useful
* How to get started quickly and securely
* Common workflows

The objective here is to **engage and enable our users to get started** and work with our API securely and effectively.

On the other hand, **Reference documentation** provides comprehensive information about the intricacies of our API:

* A list of all the resources and the available methods
* Data schemas description for both requests and responses
* HTTP error codes and how to handle them
* Security means and implementation
* Rate limiting information
* Code samples

Keeping all of that in mind, an API documentation should provide, at least, the following information:

| Type of Documentation                                                                                           | Topics\*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>Hands-on documentation</strong><br>(<em>traditionally referred as Conceptual documentation</em>)</p> | <ol><li>Overview</li><li>Quick Start/Getting Started<br><em>Note: Include security procedure</em>s</li><li>How-Tos/Use-Case Tutorials</li><li>FAQ</li></ol>                                                                                                                                                                                                                                                                                                                                                                                                                |
| Reference documentation                                                                                         | <ol><li>Overview</li><li>Authentication and Authorization</li><li><p>Endpoints and Methods</p><ol><li>Request Parameters</li><li>Response Schema</li><li>Request/Response Examples (beyond just schema, actual JSON/XML bodies)</li></ol></li><li>Error Codes and Error Handling</li><li>Rate Limiting and Thresholds</li><li>Code Examples</li><li>Glossary</li><li>Best Practices</li><li>Changelog</li><li>SDKs/Libraries (if available, with links and usage info)</li><li>Environments (e.g., Sandbox, Production URLs)</li><li>Support/Contact Information</li></ol> |

{% hint style="success" %}
**Recommendation**\
**R**ead the appendix sections to refresh what you have just read, and read this section again. It may help to visualize the API docs better.
{% endhint %}

**Think about it this way:**

> An API describes a group of _available resources_ (those paths on our server, remember?) and _which HTTP methods are available_ for our customers to use in the API's _request-response architecture_.
>
> So, _for every resource we'll have specific methods available_ to work with. These methods will ask for or transfer data from one system to another. In other words, every piece of data, requested or sent, will follow a predefined _data structure or schema_ (not as raw data) with its data types, descriptions, examples, etc.
>
> Communication can fail or not end successfully, so our HTTP methods have to be able to inform users about it. How? Sending back the specific _error code and message_ corresponding to the result of the request/responset.&#x20;
>
> All of this happens in a context where users or systems must be authenticated and authorized (or rejected) and within the time, call requests, and other limits imposed by the API design to handle the amount of allowed API calls. (Nobody wants to saturate our API!)
>
>

### Think about it this way

### How is it in the Real World?

Here's what I discovered when I looked at real API documentation in the wild: companies follow different naming conventions (with some touchpoints) to convey their API content. So remember that I said that:

> an API documentation should provide, at least, the following information

What does it mean? It means that **we can provide the information under different sections' naming** (and even add more sections or merge them!) as far as we address our API business goals and users' needs. In other words:

> _Know your API's business, know your users' needs_.

The previous list of topics represents the main topics to cover in your API documentation topics, but it is not written in stone. Your API documentation have to address specific needs. So, &#x6B;_&#x6E;ow your API's business, know your users' needs_... _Then, craft and test!_

For example, if your customer or support department points out an increasing demand from customer to have specific API workflows documented, it makes sense to add them in your tutorials' section. Or, provide all the information regarding _Endpoint, Methods_ and _Code Examples_ under a single section, including _Error Codes and Error Handling_.

> _**Know your API's business, know your users' needs.**_

## Final Thoughts

Making sense of what we learn helps us to go further and take the next step. If APIs and API documentation seem like a complicated topic, think of it as a means of sharing with your users the story of your API, the story of how your API supports them to succeed.

This framework helped me make sense of API documentation—I hope it does the same for you.
