## Stories

### Available actions

```
GET /api/v2/stories/:id
POST /api/v2/stories
PUT /api/v2/stories/:id
DELETE /api/v2/stories/:id
```

### Editable attributes

- `title`: {String} The title of the story.
- `comment`: {String} The comment of the story, either this or the `url` must be present.
- `url`: {String} The URL to the story, either this or the `comment` must be present.

### Linked resources

- `comments`: {Comment} The comments immediately attached to this story.
- `user`: {User} The user that submitted the story.
- `upvotes`: {Upvote} The upvotes that this story has received.
- `downvotes`: {Downvote} The downvotes that this story has received.
