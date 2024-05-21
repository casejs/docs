---
id: angular
---

# Quick start with Angular

Give a proper backend to your Angular app.

:::warning

This quick start guide focuses exclusively on the **frontend**. To ensure the functionality of this code, your Manifest backend must be [up and running](install.md) at `http://localhost:1111`.

:::

# 1. Create a Angular app

If you already have your Angular app up and running, skip this step.

We will use the [Angular CLI](https://angular.io/cli) to create a new Angular project. You can replace `my-client` by the name of your front-end app.

```
ng new my-client
cd my-client
ng serve
```

# 2. Install CASE SDK

Install the JS SDK from the root of your Angular app.

```
npm i @manifest/sdk
```

# 3. Use it in your app

In this example, we are using a Pokémon entity [created previously](entities.md). Replace it by your own entity.

```js
// app.component.ts

import { Component } from '@angular/core'
import Manifest from '@manifest/sdk'

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  pokemons: { id: number, name: string }[] = []

  async ngOnInit() {
    // Init SDK.
    const manifest = new Manifest()

    // Fetch the list of Pokemons.
    this.pokemons = await manifest.from('pokemon').find()
  }
}
```

And in the template:

```html
<ul>
  <li *ngFor="let pokemon of pokemons">{{ pokemon.name }}</li>
</ul>
```

Checkout the [SDK doc](connect.md) to see more usages of the SDK: CRUD operations, file upload, authentication,
