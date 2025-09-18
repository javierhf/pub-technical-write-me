# Appendix

## Appendix

### API Core Concepts

In the following table, you will find basic API-related vocabulary descriptions:

| API Vocabulary                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Resources**                     | <p>Paths on a server where the API stores and provides data. For example: <code>/users</code>, <code>/users/{id}</code>, and <code>/{id}/products</code>.</p><p>Think of them as unique URLs for specific pieces of information.</p>                                                                                                                                                                                                                                                               |
| **Method**                        | <p>The action you want to perform on a resource, defined by an HTTP verb. The most common ones are:</p><ul><li><code>GET</code> - To <strong>read</strong> a resource.</li><li><code>POST</code> - To <strong>create</strong> a new resource.</li><li><code>PUT</code> - To <strong>completely replace</strong> or update a resource.</li><li><code>DELETE</code> - To <strong>remove</strong> a resource.</li><li><code>PATCH</code> - To <strong>partially update</strong> a resource.</li></ul> |
| **Request**                       | A structured message sent by a client (System A) to a server (System B) . This message includes the desired **Method**, the **Resource** path, and sometimes data. An example is: `HTTP GET http://www.appdomain.com/users`.                                                                                                                                                                                                                                                                       |
| **Response**                      | The structured answer a server (System B) sends back to a client (System A) after receiving a **Request**. It includes an HTTP **Status Code**, an optional message, and the requested data. The most common data formats are **JSON** and **XML**.                                                                                                                                                                                                                                                |
| **Status Codes** and **Messages** | <p>HTTP protocol numeric codes and messages that tell you the result of a <strong>Request</strong> whether a request was successful, failed, or needs more information.</p><p>The codes are grouped into five categories: <code>1xx</code> (Informational), <code>2xx</code> (Success), <code>3xx</code> (Redirection), <code>4xx</code> (Client Errors), and <code>5xx</code> (Server Errors).</p>                                                                                                |
| **Authentication**                | The process of verifying a user’s or client’s identity. It’s like showing your ID to prove you are who you say you are before you can access an API.                                                                                                                                                                                                                                                                                                                                               |
| **Authorization**                 | The process of checking if an authenticated user or client has permission to access a specific resource or perform a certain action.                                                                                                                                                                                                                                                                                                                                                               |
| **Data Structure** or **Schema**  | <p>The blueprint or rules for organizing the data that is exchanged between the client and the server. It defines what fields are required, their data types, and how the information should be organized.</p><p>The most popular formats for this are <strong>JSON</strong> and <strong>XML</strong>.</p>                                                                                                                                                                                         |

### Visual API Workflow (Epic Alternative Diagram)

<figure><img src="../../../.gitbook/assets/Gemini_Generated_Image_v2zxgov2zxgov2zx.png" alt=""><figcaption></figcaption></figure>

### Python API Code Example

In the following Python code example, you will find a simple API code with explanatory comments:

```python
from flask import Flask, request, jsonify

# This line creates our web application. Think of it like opening our pet store's front door
# ready to receive visitors (requests).
app = Flask(__name__)

# --- Our Pet Store's "Database" (just a simple list for this example) ---
# This is where we keep track of our pets. Each pet has an ID, a name, a species, and a status.
# In a real store, this would be a proper database.
pets = [
    {"id": "p1", "name": "Buddy", "species": "dog", "status": "available"},
    {"id": "p2", "name": "Whiskers", "species": "cat", "status": "available"},
    {"id": "p3", "name": "Goldie", "species": "fish", "status": "adopted"},
]

# --- API Endpoint: Get All Pets or a Specific Pet ---
# This is like asking "What pets do you have?" or "Tell me about pet p1?"
# The address for this is typically '/pets' or '/pets/<pet_id>'
@app.route('/pets', methods=['GET'])
def get_pets():
    # If someone asks for all pets (e.g., visiting '/pets'), we give them the full list.
    return jsonify(pets)

@app.route('/pets/<string:pet_id>', methods=['GET'])
def get_pet(pet_id):
    # This loop goes through our pet list to find the one with the matching ID.
    for pet in pets:
        if pet['id'] == pet_id:
            # If we find the pet, we show its details.
            return jsonify(pet)
    
    # --- Error Handling Example 1: Pet Not Found ---
    # If we look through all our pets and can't find the one requested,
    # we send back a "404 Not Found" message. This tells the requester
    # that the pet ID they provided doesn't exist in our store.
    return jsonify({"error": "Pet not found"}), 404

# --- API Endpoint: Update an Existing Pet ---
# This is like telling the store, "I want to change something about pet p1."
# The address is '/pets/<pet_id>' and we use the 'PUT' method.
@app.route('/pets/<string:pet_id>', methods=['PUT'])
def update_pet(pet_id):
    # We expect the person sending the request to also send us the new details
    # for the pet in a structured format (JSON).
    data = request.get_json()
    
    # --- Error Handling Example 2: Missing Data ---
    # We check if they actually sent us any new information. If 'data' is empty,
    # it means they didn't provide any updates, so we send a "400 Bad Request" error.
    if not data:
        return jsonify({"error": "No data provided for update"}), 400

    # Find the pet in our list that matches the ID.
    for pet in pets:
        if pet['id'] == pet_id:
            # Once found, we update its information with the new data received.
            # For example, if 'name' was in the data, we update the pet's name.
            pet.update(data)
            # Then we send back the updated pet's details as confirmation.
            return jsonify(pet)
            
    # If we can't find the pet to update, it's another "404 Not Found" error.
    return jsonify({"error": "Pet not found"}), 404

# --- How to Run Our Pet Store API ---
# This part makes our pet store "open for business" on your computer.
# When you run this Python file, it starts a small web server.
# You can then access it through your web browser or other tools.
if __name__ == '__main__':
    app.run(debug=True) # 'debug=True' is helpful for development, shows more info if something goes wrong.

```

### API Design Approaches

In the following table, you'll find an informative description of the different API design approaches:

| API Coding Approach  | Description                                                                                                                                                                                                                             | Pros                                                                                                                                                                                                                                                                                                                | Cons                                                                                                                                                                                                                                   |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Code-First**       | You start by writing your API's implementation code, then use tools or annotations within your code to generate the API specification (like OpenAPI/Swagger) automatically. The code is the source of truth.                            | <p>- <strong>Faster development:</strong> Jump straight into coding with auto-generated documentation.</p><p>- <strong>Always synchronized:</strong> Documentation updates automatically with code changes.</p>                                                                                                     | <p>- <strong>Design can be an afterthought:</strong> May lead to less consistent or well-thought-out API designs.</p><p>- <strong>Tool dependency:</strong> Relies heavily on code generation tools, which might have limitations.</p> |
| **API Design-First** | You begin by designing and defining your API using an API specification language (like OpenAPI/Swagger, RAML, API Blueprint) before writing any code. Tools then generate boilerplate code or documentation from this specification.    | <p>- <strong>Improved API quality:</strong> Forces thoughtful design from the start.</p><p>- <strong>Early feedback:</strong> Stakeholders can review the API design before development begins.</p><p>- <strong>Parallel development:</strong> Frontend and backend teams can work concurrently using the spec.</p> | <p>- <strong>Slower initial setup:</strong> Requires an extra design step before coding begins.</p><p>- <strong>Syncing challenges:</strong> If code deviates from the spec, manual updates are needed.</p>                            |
| **Hybrid Approach**  | Combines elements of both Code-First and Design-First. You might start with a high-level design document or a rough spec, then implement the core API with Code-First tools, and finally refine the specification and code iteratively. | <p>- <strong>Balances speed and quality:</strong> Get started quickly but still benefit from design principles.</p><p>- <strong>Flexibility:</strong> Can adapt to project needs and team strengths.</p>                                                                                                            | <p>- <strong>Complexity:</strong> Can be harder to manage the workflow and keep everything synchronized.</p><p>- <strong>Requires discipline:</strong> Needs a clear process to ensure design and code remain aligned.</p>             |

### OpenAPI and Arazzo Specifications

In the following table you'll find a description of the OpenAPI and Arazzo specifications and the best use cases for them:

| API Specification               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                       | Best Use Cases                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OpenAPI Specification (OAS)** | A widely adopted, language-agnostic standard for **describing RESTful APIs**. It focuses on defining the API's surface: endpoints, operations, parameters, responses, and security schemes. It's essentially the blueprint for _what_ an API does.                                                                                                                                                                                                | <p>- <strong>Defining API Contracts:</strong> Creating a clear, machine-readable definition of a REST API.</p><p>- <strong>Automated Tooling:</strong> Generating documentation (Swagger UI), client SDKs, server stubs, and testing tools.</p><p>- <strong>Design-First Development:</strong> Collaborating on API design before coding begins.</p><p>- <strong>API Discovery &#x26; Consumption:</strong> Helping developers understand and integrate with APIs quickly.</p>                                                                                                                                                                                                                                                                                                        |
| **Arazzo Specification**        | A new specification focused on **describing API-level callbacks, webhooks, and asynchronous API interactions**. Unlike OpenAPI, which defines the initial request-response contract, Arazzo describes the _events and messages_ that an API might send or receive asynchronously _after_ an initial request, often involving a client-provided callback URL. It provides a formal way to define "reverse calls" or event-driven patterns in APIs. | <p>- <strong>Defining Webhooks:</strong> Clearly specifying how an API will notify a client of events.</p><p>- <strong>Asynchronous API Workflows:</strong> Documenting long-running processes where the API calls back to the client upon completion or status change.</p><p>- <strong>Event-Driven Architectures:</strong> Formalizing the structure of events and callback messages.</p><p>- <strong>Microservices Communication:</strong> Detailing asynchronous inter-service communication patterns where one service triggers actions in another via callbacks.</p><p>- <strong>Enhancing OpenAPI:</strong> Arazzo is designed to complement OpenAPI, describing the asynchronous <em>behavior</em> of an API that OpenAPI defines the synchronous <em>interface</em> for.</p> |

### OpenAPI Specification Example

The following piece of an incomplete OpenAPI specification file shows some of those objects:

```yaml
openapi: 3.0.4
info:
externalDocs:
servers:
tags:
  /pet:
    put:
      tags:
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
paths:
components:
```

{% hint style="info" %}
**Complete openAPI specification**

Check a [complete example](https://editor.swagger.io/) of an openAPI specification to have a wider view of its content.
{% endhint %}
