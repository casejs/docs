---
id: rest-api
---

# REST API

An alternative to the [JS SDK](javascript-sdk.md) to connect to your backend is through the **REST API**.

The slug of the entity is by default the plural dasherized name of the entity, but you can change it in the [params](entities.md#entity-params)

All entities start with the `api/dynamic` prefix. Ex: `http://localhost:1111/api/dynamic/cats`

## GET /:slug

Gets a list of items from an entity.

### Params

You can filter by [property](properties.md) to refine the list of items. Use suffix to pass logic to it:

| Option     | Description           | Example                    |
| ---------- | --------------------- | -------------------------- |
| **\_eq**   | equals                | `isActive_eq=true`         |
| **\_gt**   | greater than          | `birthdate_gt=2020-01-01 ` |
| **\_gte**  | greater than or equal | `age_gte=4`                |
| **\_lt**   | less than             | `amount_lt=400`            |
| **\_lte**  | less than or equal    | `amount_lte=400`           |
| **\_like** | like                  | `name_like=%bi%`           |
| **\_in**   | included in           | `customer_in=1,2,3`        |

## GET /:slug/:id

Get a single item.

## POST /:slug

Create a new item.

Provide a Request Payload in JSON:

```json
{
  "age": 2
  "name": "Milo"
}
```

## PUT /:slug/:id

Update an item.

Provide a Request Payload in JSON:

```json
{
  "age": 2
  "name": "Milo"
}
```

## DELETE /:slug/:id

Delete an item.
