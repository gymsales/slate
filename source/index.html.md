---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - companies
  - errors

search: true
---

# Introduction

GymSales is a fully hosted lead management system for the fitness industry. We provide a [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) API built on [pragmatic RESTful design](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api) principles.

Our API uses resource-oriented URLs that leverage built in features of HTTP, like authentication, verbs and response codes. All request and response bodies are [JSON](http://en.wikipedia.org/wiki/JSON) encoded, including error responses. Any off-the-shelf HTTP client can be used to communicate with the API.

We believe an API is a user interface for a developer - accordingly, we've made sure our API can be easily explored from the browser!

## JSON Bodies

All `POST`, `PUT` requests are [JSON](http://en.wikipedia.org/wiki/JSON) encoded and must have have content type of `application/x-www-form-urlencoded` or `application/json`, or the API will return a `415 Unsupported Media Type` status code.

```shell
curl -u email:password https://login.gymsales.net/api/v1/users/12345 \
    -X PUT \
    -H 'Content-Type: application/json' \
    -d '{"first_name":"John"}'
```

>Raw HTTP Request:

```http
PUT /api/v1/users/12345 HTTP/1.1
Authorization: Basic ZW1haWw6cGFzc3dvcmQ=
Host: login.gymsales.net
Accept: */*
Content-Type: application/json
Content-Length: 21

{"first_name":"John"}
```

## HTTP Verbs

We use standard HTTP verbs to indicate intent of a request:

*   `GET` - To retrieve a resource or a collection of resources
*   `POST` - To create a resource
*   `PUT` - To modify a resource
*   `DELETE` - To delete a resource

## Limited HTTP Clients

If you are using an HTTP client that doesn't support `PUT`, `PATCH` or `DELETE` requests, send a `POST`request with an `X-HTTP-Method-Override` header specifying the desired verb.

```shell
curl -u email:password https://login.gymsales.net/api/v1/users/1234 \
    -X POST \
    -H "X-HTTP-Method-Override: DELETE"
```

>Raw HTTP Request:

```http
POST /api/v1/users/12345 HTTP/1.1
Authorization: Basic ZW1haWw6cGFzc3dvcmQ=
Host: login.gymsales.net
Accept: */*
Content-Type: application/json
Content-Length: 21
X-HTTP-Method-Override: DELETE
```

## Responses

All response bodies are [JSON](http://en.wikipedia.org/wiki/JSON) encoded.

>A single resource is represented as a JSON object:

```json
{
  "field1": "value",
  "field2": true,
  "field3": []
}
```

>A collection of resources is represented as a JSON array of objects named `collection` and a `pagination` object with total pages and total entries fields:

```json
{
  "collection": [
    {
      "field1": "value",
      "field2": true,
      "field3": []
    },
    {
      "field1": "another value",
      "field2": false,
      "field3": []
    }
  ],
  "pagination": {
    "total_pages": 1,
    "total_entries": 2
  }
}
```

Timestamps are in company time zone and formatted as [ISO8601](http://en.wikipedia.org/wiki/ISO_8601).

Unset fields will be represented as a `null` instead of not being present. If the field is an array, it will be represented as an empty array - ie `[]`.

## HTTP Status Codes

We use HTTP status codes to indicate success or failure of a request.

Success codes:

*   `200 OK` - Request succeeded. Response included
*   `201 Created` - Resource created. URL to new resource in Location header
*   `204 No Content` - Request succeeded, but no response body

Error codes:

*   `400 Bad Request` - Could not parse request
*   `401 Unauthorized` - No authentication credentials provided or authentication failed
*   `403 Forbidden` - Authenticated user does not have access
*   `404 Not Found` - Resource not found
*   `415 Unsupported Media Type` - POST/PUT/PATCH request occurred without a `application/json`content type
*   `422 Unprocessable Entity` - A request to modify or create a resource failed due to a validation error
*   `500, 501, 502, 503, etc` - An internal server error occured

# Authentication

This API is authenticated using [HTTP Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication) over HTTPS. Any requests over plain HTTP will fail.

A user's email address and password can be provided as auth credentials

All requests are associated with a specific user in GymSales and permissions are limited to that user's capabilities.

```shell
$ curl -u email:password https://login.gymsales.net/api/v1/
```

```http
POST /api/v1/users/12345 HTTP/1.1
Authorization: Basic ZW1haWw6cGFzc3dvcmQ=
```

GymSales expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic <credentials>`, where credentials is the base64 encoding of id and password joined by a single colon (:).


# Resources

