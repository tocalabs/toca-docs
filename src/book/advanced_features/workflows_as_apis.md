# Workflows as APIs

![A simple connector](/src/assets/book/connector_overview.png)
Connectors allow us to trigger a workflow when a specific URL is hit with a certain [HTTP method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods). This allows us to implement anything, from something as simple as a fileserver, to a full HTTP API.

![A simple connector](simple-connector.gif)

Every instance of a connector has a **handler** which receives a HTTP request at a given route, and optionally one or more **responses** which respond to the requester.

> **Warning** ⚠️
> Connector routes can only have one path segment. At the time of writing, there is a known limitation regarding saving a connector with a route consisting of **multiple path segments** (e.g. multiple/path/segments). The workflow can be saved and published with multiple path segments, but it will not be functional.

## Toca connectors

While we can create our own connectors in the TDK, Toca ships with a few default connectors to get us started. These share some standard behaviours.

### Handler

Handlers are represented by a circular node.
#### Output

The default connectors provide many variables which can be used as inputs to activities in workflows. We may often find ourselves using QueryParameters and Headers from the connector's handler to conditionally execute activities.


### Response

Responses are represented by square nodes.
#### Code

Each connector can respond with different status codes. This functionality can be particularly useful when combined with exclusive nodes to control which response code is sent to the requester depending on activity outputs.
#### Body

Sometimes, we may want to respond with more than just a status code. The *body* field of the response allows us to return arbitrary text to the requester.

#### Method

Toca connectors can only be called by their corresponding HTTP method - a GET request cannot call a POST connector.

> **Note** 🗒️
> While you can implement a [REST API](https://aws.amazon.com/what-is/restful-api/) with connectors, the default connectors do not enforce REST standards: for example, a DELETE connector can take a request Body, and a GET connector does not need to be idempotent.

## Putting it all together

:video{src="/src/assets/book/connector_demo.webm"}

It's very easy to create a basic connector which provides a response to the requester.
1. Create a workflow with start and stop nodes.
2. Drag a connector from the sidebar - the most commonly used one is the HTTP GET connector. This creates a handler.
	1. You can customise the API route by clicking on the handler.
3. Link the connector node (the handler) to the start node.
4. Click on the handler, and click the tooltip button to create a response node.
	1. You can specify the response body by clicking on the response node.
5. Link your final activity to the response node.
6. Link your response node to the stop node.
