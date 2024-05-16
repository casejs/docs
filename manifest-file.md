---
id: manifest-file
---

# The backend.yml file

The [install script](install.md) creates a `backend.yml` file with the description of your backend. [YAML](https://en.wikipedia.org/wiki/YAML) is a very simple markup language.

Let's take this `backend.yml` file as an example:

```yaml
name: A simple blog

entities:
  🗒️ Post:
    properties:
      - title
      - content
    belongsTo:
      - Author

  🧑🏽‍🦱 Author:
    properties:
      - name
      - email
      - bio
```

- The property **name** is the name of your app
- The **entities** property is an object that expects the list of your entities
- And yes, you can use emojis 😎
