## Earned Colors

### Available actions

```
GET /api/v2/earned_colors/:id
```

### Attributes

- `name`: {String} The name of the earned color.
- `description`: {String} The description of the color, usually how the color was earned.
- `value`: {Array[Number]} A 3-item Array containing Numbers for the RGB values of the color.

### Linked resources

- `users`: {User} The users that have earned the given color.
