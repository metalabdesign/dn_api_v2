## Stories

### Available actions

```
GET /api/v2/stories/:id
POST /api/v2/stories
PUT /api/v2/stories/:id
DELETE /api/v2/stories/:id
```

### Attributes

- `title`: {String} The title of the story.
- `comment`: {String} The comment of the story in Markdown, either this or the `url` must be present.
- `url`: {String} The URL to the story, either this or the `comment` must be present.
- `badge`: {String} The name of the badge applied to the current story.
- `comment_html`: {String} The rendered `comment` value of this story.
- `pinned_at`: {Date} The pinned date of when this story was pinned.
- `sponsored`: {Boolean} Whether or not this is a sponsored story.
- `vote_count`: {Number} The number of points this story has.
- `hostname`: If the story has a `url`, this is a sanitized hostname of the destination URL.

### Editable attributes

- `title`
- `comment`
- `url`

### Linked resources

- `comments`: {Comment} The comments immediately attached to this story.
- `user`: {User} The user that submitted the story.
- `upvotes`: {Upvote} The upvotes that this story has received.
- `downvotes`: {Downvote} The downvotes that this story has received.
