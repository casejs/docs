# Relations

Add a relationship between two [entities](entities.md), like an _Invoice_ that belongs to a _Customer_, a _Pet_ that belongs to an _Owner_, etc.

:::note

As of today, only the _BelongsTo_ and thus its opposite _hasMany_ are available.

_ManyToMany_ relationships are coming soon.

:::

## BelongsTo relationship

### Syntax

This is a standard _HasMany_ / _BelongsTo_ relationship between **User** and **Cat** entities.

Each **User** can have several **Cat** items. A **Cat** must have a **User**.

```yaml
😃 User:
properties:
  - name

😺 Cat:
  properties:
    - name
  belongsTo:
    - User
```

As for the [properties](properties.md), there is a short and a long syntax. The long syntax allows you pass params to it:

```yaml
🐶 Dog:
  properties:
    - name
  belongsTo:
    - { name: Owner, entity: User, eager: true }
```

## Relation params

You can pass arguments using the long syntax:

| Option     | Default     | Type    | Description                                                                                                                      |
| ---------- | ----------- | ------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **name**   | Entity name | string  | The name of the relation                                                                                                         |
| **entity** | -           | string  | The class name of the entity that the relationship is with                                                                       |
| **eager**  | `false`     | boolean | Whether the relationship should be eager loaded. Otherwise, you need to explicitly request the relation in the client SDK or API |
