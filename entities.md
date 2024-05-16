---
id: entities
title: Create an entity
---

# Create an entity

An entity is an object often linked to a real world concept like users, customers, videos etc.

All entities are located in the `backend.yml` file under the **entities** property.

## Syntax

Let's see a simple example:

```yaml
# manifest/backend.yml
name: A pet app

entities:
  😺 Cat:
    properties:
      - name
  🐶 Dog:
    properties:
      - name
```

This file will generate the **Cat** and **Dog** entity both with a `name` property. You can now add your own pets trough the admin panel !

Dummy data is crucial for app development and testing. You can generate dummy data for all your entities with the simple command:

```
npm run seed
```

:::warning

The seed replaces the previous data by the new one and thus should never be used in production.

:::

## Entity params

You can pass different arguments to configure your entities. Example:

```yaml
entities:
  👤 Member:
    seedCount: 200
    mainProp: number
    properties:
      - name
      - number
      - email
```

| Option           | Default                    | Type   | Description                                                                                               |
| ---------------- | -------------------------- | ------ | --------------------------------------------------------------------------------------------------------- |
| **nameSingular** | _singular lower case name_ | string | he singular lowercase name of your entity. Used widely on the admin panel.                                |
| **namePlural**   | _plural lower case name_   | string | The plural lowercase name of your entity. Used widely on the admin panel. Default: plural lowercase name. |
| **slug**         | _plural dasherized name_   | string | The kebab-case slug of the entity that will define API endpoints.                                         |
| **mainProp**     | _first string field_       | string | Identifier prop. Used widely on the admin panel                                                           |
| **seedCount**    | `50`                       | number | the number of entities to seed when running the seed command.                                             |
