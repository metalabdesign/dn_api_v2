## Blog Posts

Designer News has a blog, and that blog can be accessed through the API.

### Avaialble actions

```
GET /api/v2/posts
GET /api/v2/posts/:id
```

### Attributes

- `body`: {String} The body of the blog post in Markdown.
- `published_at`: {Date} The Date of when the post was published.
- `story_url`: {String} The URL of the story for the blog post’s comments.
- `title`: {String} The title of the blog post.

### Linked resources

- `user`: {User} The user that authored the blog post.
