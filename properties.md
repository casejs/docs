---
id: properties
---

# Add properties to an entity

Properties are the characteristics of your [entities](entities). For example, a **Product** can have properties like `name`, `description`, `price`...

## Syntax

You can add the properties to your entities in the [backend.yml file](manifest-file)

```yaml
name: Blog about cats
entities:
  📝 Post:
    properties:
      - name # Short syntax for string type.
      - { name: content, type: text } # Property type specified.
      - { name: publishedAt, type: date }
      - { name: authorEmail, type: email, hidden: true } # Extra options.
```

## Property params

You can pass arguments using the long syntax:

| Option      | Default  | Type       | Description                                                             |
| ----------- | -------- | ---------- | ----------------------------------------------------------------------- |
| **type**    | "string" | _PropType_ | The [Property type](#property-types) (text, number, email, location...) |
| **hidden**  | `false`  | boolean    | If the property should be hidden in the API response                    |
| **options** | {}       | Object     | Specific options depending on **type**                                  |

## Property types {#property-types}

Each property has a **type** that represent real-world usages. Some of them have specific options.

### String

A simple string.

```yaml
- { name: firstName, type: string }

# Short syntax, same as above.
- firstName
```

<div class="show-result">
![Text property type: field and yield](./assets/images/prop-text.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![text input](./assets/images/input-text.svg)
    ![text yield](./assets/images/display-text.svg)
  </div>
</div>

---

### Textarea

Textarea field for medium size texts.

```yaml
- { name: description, type: text }
```

<div class="show-result">
![textarea property type: field and yield](./assets/images/prop-textarea.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![textarea input](./assets/images/input-textarea.svg)
    ![textarea yield](./assets/images/display-textarea.svg)
  </div>
</div>

### Number

A numerical value.

```yaml
- { name: age, type: number }
```

<div class="show-result">
![Number property type: field and yield](./assets/images/prop-number.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![number input](./assets/images/input-number.svg)
    ![number yield](./assets/images/display-number.svg)
  </div>
</div>

---

### Link

An URL that links to an external page.

```yaml
- { name: website, type: link }
```

<div class="show-result">
![link property type: field and yield](./assets/images/prop-link.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![link input](./assets/images/input-link.svg)
    ![link yield](./assets/images/display-link.svg)
  </div>
</div>

---

### Money

A money field with a currency.

```yaml
- { name: price, type: money, options: { currency: 'EUR' } }
```

<div class="show-result">
![currency property type: field and yield](./assets/images/prop-currency.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![currency input](./assets/images/input-currency.svg)
    ![currency yield](./assets/images/display-currency.svg)
  </div>
</div>

##### Parameters

| Option       | Default | Type   | Description                                                                                      |
| ------------ | ------- | ------ | ------------------------------------------------------------------------------------------------ |
| **currency** | _USD_   | string | [ISO 4217 currency code](https://en.wikipedia.org/wiki/ISO_4217#List_of_ISO_4217_currency_codes) |

---

### Date

Basic date field.

```yaml
- { name: startDate, type: date }
```

<div class="show-result">
![date property type: field and yield](./assets/images/prop-date.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![date input](./assets/images/input-date.svg)
    ![date yield](./assets/images/display-date.svg)
  </div>
</div>

---

### Email

```yaml
- { name: email, type: email }
```

<div class="show-result">
![email property type: field and yield](./assets/images/prop-email.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![email input](./assets/images/input-email.svg)
    ![email yield](./assets/images/display-email.svg)
  </div>
</div>

---

### Boolean

For any field with a "true or false" value.

```yaml
- { name: isActive, type: boolean }
```

<div class="show-result">
![boolean property type: field and yield](./assets/images/prop-boolean.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![boolean input](./assets/images/input-boolean.svg)
    ![boolean yield](./assets/images/display-boolean.svg)
  </div>
</div>

---

### Password

Password field.

```yaml
- { name: password, type: password }
```

![password property type field](./assets/images/prop-pw.svg ':class=is-hidden-tablet')

:::danger

You should never ever store a password on clear text.

:::

### Choice

A given choice of options.

```yaml
- { name: sex, type: choice, options: { values: [male, female] } }

# Sequential if the values are ordered in a logical sense..
- {
    name: status,
    type: choice,
    options: { values: [draft, submitted, published], sequential: true }
  }
```

##### Display: 'label'

<div class="show-result">
![enum-label property type: field and yield](./assets/images/prop-enum-label.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![enum-label input](./assets/images/input-enum-label.svg)
    ![enum-label yield](./assets/images/display-enum-label.svg)
  </div>
</div>

##### Display: 'progress-bar'

<div class="show-result">
![enum-pb property type: field and yield](./assets/images/prop-enum-pb.svg ':class=is-hidden-tablet')

  <div class="is-hidden-desktop"> 
    ![enum-pb input](./assets/images/input-enum-pb.svg)
    ![enum-pb yield](./assets/images/display-enum-pb.svg)
  </div>
</div>

##### Parameters

| Option         | Default   | Type     | Description                                            |
| -------------- | --------- | -------- | ------------------------------------------------------ |
| **values**     | _(empty)_ | String[] | An array of strings representing the available choices |
| **sequential** | `false`   | boolean  | Specifies if the values are ordered in a logical sense |

### Location

The location type consists in a object with `lat` and `lng` coordinates.

```yaml
- { name: location, type: location }
```
