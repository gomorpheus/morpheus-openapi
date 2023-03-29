---
title: Getting Started with the Morpheus API
---
This document describes the Morpheus API protocol and the available endpoints. Sections are organized in the same manner as they appear in the Morpheus UI.

The Morpheus API is an HTTP interface for interacting with the Morpheus appliance. It provides a RESTful interface where `GET` reads, `POST` creates, `PUT` updates and `DELETE` destroys resources.

This is an example of a Morpheus API request that retrieves details about a User.

# HTTP Request
`GET $serverUrl/api/users/:id`

HTTP Request describes the method and path of the endpoint. Most endpoints have a path formatted as `/api/:resources/:id`.

# URL Parameters
[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "id",
    "0-1": "ID of the User."
  },
  "cols": 2,
  "rows": 1
}
[/block]
URL Parameters are variables which are included inside the path of the request.

# HTTP Headers
[block:parameters]
{
  "data": {
    "h-0": "Header",
    "h-1": "Description",
    "0-0": "Authorization",
    "0-1": "Use the format `BEARER ${access_token}`. \n\nExample: `Authorization: BEARER e1d62c34-f7f5-4713-a874-31491e7707de`. Most endpoints require this header. Some exceptions include Authentication and Setup.",
    "1-0": "Content-Type",
    "1-1": "Use `application/json` for `POST` and `PUT` requests. This is needed to ensure your JSON payload is parsed. Exceptions to this rule include file uploads where `application/x-www-form-urlencoded` and `application/octet-stream` should be used instead."
  },
  "cols": 2,
  "rows": 2
}
[/block]
HTTP Headers are used to authorize the acting user via a valid access token, and to describe the type of content being sent, which is typically JSON.

# Query Parameters
[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "phrase",
    "0-1": "If specified will return a partial match on name."
  },
  "cols": 2,
  "rows": 1
}
[/block]
Query Parameters are variables included in the query string portion of the request url, after the `?` and they are delimited by `&`. Be sure to html encode your parameters and values!

# JSON Parameters
[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "name",
    "0-1": "A unique string."
  },
  "cols": 2,
  "rows": 1
}
[/block]
JSON Parameters define the variables to be included in the body of the request. These are typically under the the context of an object, such as "contact".

# HTTP Response
The HTTP status *200 OK* will be returned when a request is successful and an HTTP Error status will be returned when a request fails.

Most endpoints respond with Content-Type: `application/json` and a body that contains JSON data.

This is an example of an API response that retrieves a Contact record by ID.

# Example
```
curl "$serverUrl/api/monitoring/contacts/1" \
  -H "Authorization: BEARER $accessToken"
```
The above command returns HTTP 200 and JSON structured like this:
```
{
  "contact": {
    "id": 1,
    "name": "Morpheus Admin",
    "emailAddress": "admin@morpheusdata.com",
    "smsAddresss": null
  }
}
```
This is an example of a successful response that contains the specified record.

Error Example
```
curl "$serverUrl/api/monitoring/contacts/999999" \
  -H "Authorization: BEARER $accessToken"
```
The above command returns HTTP 404 and JSON structured like this:

```
{
  "success": false,
  "msg": "Contact not found for this account"
}
```
This is an example of a 404 error response returned when the specified record was not found.