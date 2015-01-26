## Common Responses

Because v2 of the Designer News API spec conforms to the [JSON API standard](http://jsonapi.org),
response formats and error codes are similar among all resources. JSON API also allows clients
to request any number of linked resources along with the primary payload. (For example,
you can receive all users and comments in the same payload as requesting a group of stories.)

This leads to an API that is simple, concise, and predictable.

Here are a few notes for working with our API:

### All response resources are plural

Even if you only request a single resource, e.g. `GET /api/v2/users/1`, the first key of the
response will be plural. Example:

```json
{
  "users": {
    "id": "1",
    "first_name": "Kelly",
    "last_name": "Sutton"
  }
}
```

In the case that multiple resources have been requested, e.g. `GET /api/v2/users/1,2,3`, the response will be an array:

```json
{
  "users": [{
    "id": "1"
  },
  {
    "id": "2"
  },
  {
    "id": "3"
  }]
}
```

### Linked resources

If the requested resource links to any other resource, that resource will be links to in a `links` property.
For example, this is how a story’s author and comments are represented:

```json
{
  "stories": {
    "id": "101",
    "links": {
      "user": "1",
      "comments": ["1001", "1002", "1003"]
    }
  }
}
```

If the client wishes to understand more information about the user or the comments, new requests must be made.

### All IDs are strings

Per the [JSON API standard](http://jsonapi.org/format/#document-structure-resource-object-ids), all IDs
are strings. This may feel a bit funky at first, but it prevents unnecessary integer parsing from strings
as you build your application.

### Common response codes

All requests will yield predictable response codes in their responses.

#### 200 OK

Everything is A-OK. In the case of updating a resource, all edits were performed successfully.
The response will always contain the content of the resource requests or modified.

#### 201 Create

Only applicable to POST requests to create a resource. The newly-created resource will always be returned.
Please see the [Creating Resources section of the JSON API standard.](http://jsonapi.org/format/#crud-creating-resources).

Currently, the Designer News API v2 only supports creating individual resources.

#### 204 No Content

The server understood and performed the request, but it has nothing to say.

In the contetx of a `PUT` request, the request was processed, but no attributes were updated.

In the context of a `DELETE` request, the resource was successfully deleted.

#### 400 Bad Request

HTTP 400 is used as a general catch-all for malformed requests. Please refer to the error response JSON
for more information.

#### 401 Unauthorized

Creating, updating, or deleting a resource requires authentication via an `Authorization` header.
If no header is present, or that header is invalid, an `HTTP 401` will be returned.

#### 403 Forbidden

Updating and deleting resources can only be done by admins, mods, or resource owners (like the author
of a story). If the authorized user is not able to update or delete a given resource, an `HTTP 403`
will be returned.

#### 404 Not Found

You know the drill.

#### 405 Method Not Allowed

The Designer News API v2 is a work in proress. If a client receives an `HTTP 405`, we have
not gotten around to implementing that method yet.

#### 409 Conflict

When updating or creating a resource, the given resource conflicts with another resource in the
database. This is usually triggered to prevent the double-posting of stories or comments.

#### 415 Unsupported Media Type

As the [JSON API spec declares](http://jsonapi.org/format/#document-structure), all documents
must have the `application/vnd.api+json` media type. Don’t forget to set the `Content-Type` headers
to this value when creating or updating resources.

#### 422 Unprocessable Entity

If the request has malformed JSON, you will receive this error code.

### Common error format

If the client receives a client error code (400-499), a predictable error message payload will be including.
This error message will have a human-readable message suitable for display in your application.
The error message will be in American English.

```json
{
  "error": "Only a mod, admin, or owner can update this story."
}
```
