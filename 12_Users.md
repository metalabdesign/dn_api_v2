## Users

Get information about other users. Note: there is one endpoint that is included here that does
not conform to the JSON API organization, and that is `/api/v2/me`. That endpoint returns
information about the currently authenticated user, if any.

### Available actions

```
GET /api/v2/users
GET /api/v2/users/:id
PUT /api/v2/users/:id
GET /api/v2/me
```

### Attributes

- `email`: {String} The user’s email.
- `first_name`: {String} The user’s first name.
- `last_name`: {String} The user’s last name.
- `job`: {String} The user’s job title.
- `karma`: {Number} The total karma for the given user.
- `open_links_in_new_window`: {Boolean} The user prefers to have links open in a new window.
- `receive_reply_emails`: {Boolean} Whether or not the user receives email notifications for comment replies on their stories or comments.
- `receive_digest`: {Boolean} The user receives the weekly digest.
- `twitter_name`: {String} The user’s Twitter handle, without the '@'.

### Editable attributes

- `first_name`
- `last_name`
- `email`
- `password`
- `job`
- `receive_reply_emails`stories or comments.
- `receive_digest`
- `open_links_in_new_window`
- `twitter_name`

### Linked resources

- `comments`: {Comment} The comments the user has created
- `downvotes`: {Downvote} The downvotes the user has created
- `earned_colors`: {EarnedColor} The colors the user has earned
- `invited_by`: {User} The user that the invited the specified user
- `invited_users`: {User} The users that were invited by the specified user
- `stories`: {Story} The stories the user has created
- `upvotes`: {Upvote} The upvotes the user has created

