## Common Responses

Because v2 of the Designer News API spec conforms to the [JSON API standard](http://jsonapi.org),
response formats and error codes are similar among all resources. JSON API also allows clients
to request any number of linked resources along with the primary payload. (For example,
you can receive all users and comments in the same payload as requesting a group of stories.)

This leads to an API that is simple, concise, and predictable.

Here are a few notes for working with our API:

### All responses are plural

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
  }],
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
      "comments": "1001", "1002", "1003"
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

    200 OK
    201 Created
    204 No Content
    400 Bad Request
    401 Unauthorized
    403 Forbidden
    404 Not Found
    405 Method Not Allowed
    409 Conflict
    415 Unsupported Media Type
    422 Unprocessable Entity

### Common error format

If the client receives a client error code (400-499), a predictable error message payload will be including.
This error message will have a human-readable message suitable for display in your application.
The error message will be in American English.

```json
{
  "error": "Only a mod, admin, or owner can update this story."
}
```
