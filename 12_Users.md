## Users

### Available actions

```
GET /api/v2/users/:id
GET /api/v2/users
PUT /api/v2/users/:id
```

### Editable attributes

- `first_name`: {String} The user’s first name
- `last_name`: {String} The user’s last name
- `email`: {String} The user’s email
- `password`: {String} The user’s password
- `job`: {String} The user’s job title
- `receive_reply_emails`: {Boolean} Whether or not the user receives email notifications for comment replies on their stories or comments.
- `receive_digest`: {Boolean} The user receives the weekly digest.
- `open_links_in_new_window`: {Boolean} The user prefers to have links open in a new window.
- `twitter_name`: {String} The user’s Twitter handle, without the '@'

### Linked resources

- `comments`: {Comment} The comments the user has created
- `downvotes`: {Downvote} The downvotes the user has created
- `earned_colors`: {EarnedColor} The colors the user has earned
- `invited_by`: {User} The user that the invited the specified user
- `invited_users`: {User} The users that were invited by the specified user
- `stories`: {Story} The stories the user has created
- `upvotes`: {Upvote} The upvotes the user has created
