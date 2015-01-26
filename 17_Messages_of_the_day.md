## Messages of the Day

The Message of the Day is a free-form text field at the top of Designer News. Almost anything goes.

### Available actions

```
GET /api/v2/motds
GET /api/v2/motds/:id
POST /api/v2/motds
```

### Attributes

- `message`: {String} The content of the MOTD.

### Editable attributes

- `message`

### Linked Resources

- `user`: {User} The user that created the MOTD
- `upvotes`: {MotdUpvote} The upvotes for the MOTD
- `downvotes`: {MotdDownvote} The downvotes for the MOTD
