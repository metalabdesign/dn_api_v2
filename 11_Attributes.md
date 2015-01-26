## Attributes

Each resource has one or more attributes that can be read and modified. Each attribute
will be of a certain data type. These are the following data types currently supported:

- Boolean
- String
- Number

Each attribute must be given its proper type for creation or editing.

Each resource will always have the following 4 attributes: `id`, `type`, `href`,
and `links`.

They are as follows:

- `id`: {String} The ID of the resource. Always a String.
- `type`: {String} The plural type of the current resource, e.g. "stories" or "comments"
- `href`: {String} The URL to the current resource
- `links`: {Object} An Object representing the other resources associated with this resource
