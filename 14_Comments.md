## Comments

### Available actions

```
GET /api/v2/comments/:id
PUT /api/v2/comments/:id
POST /api/v2/comments
DELETE /api/v2/comments/:id
```

### Editable attributes

- `body`: {String} The body of the comment, in Markdown.

### Linked resources

- `comments`: {Comment} The replies on the current comment.
- `comment_upvotes`: {CommentUpvote} The upvotes on the current comment.
- `comment_downvotes`: {CommentDownvote} The downvotes on the current comment.
- `parent_comment`: {Comment} The comment this comment is attach to. Either this or `story` will be present.
- `story`: {Story} The story this comment is attached to.
- `user`: {User} The user that left this comment
