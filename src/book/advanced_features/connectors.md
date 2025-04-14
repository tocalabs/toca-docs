# Webhooks in Toca: Connectors
![[connector_overview.png]]
Connectors allow us to trigger a workflow when a specific URL is hit with a certain [HTTP method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods). This allows us to implement anything, from something as simple as a fileserver, to a full HTTP API.

![A simple connector](simple-connector.gif)

Every instance of a connector has a **handler** which receives a HTTP request, and optionally one or more **responses** which respond to the requester.

## Method
## Handler output


> **Warning** ⚠️
> 
> 