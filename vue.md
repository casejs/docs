---
id: vue
---

# Quick start with Vue

Give a proper backend to your Vue.js app.

:::warning

This quick start guide focuses exclusively on the **frontend**. To ensure the functionality of this code, your Manifest backend must be [up and running](install.md) at `http://localhost:1111`.

:::

# 1. Create a Vue app

If you already have a Vue app running, you can skip this step.

We are using Vue.js v3 in this tutorial. You can replace `my-client` by the name of your front-end app

```
npm create vue@latest
cd my-client // If you called your app "my-client" when asked in the previous step
npm install
npm run dev
```

# 2. Install CASE SDK

Install the JS SDK from the root of your Vue app.

```
npm i @manifest/sdk
```

# 3. Use it in your app

In that example we are using a Pokemon entity [created previously](entities.md). Replace it by your own entity. This example uses TypeScript, you can remove the typing to have plain JS.

```js
<script lang="ts">
import Manifest from "@manifest/sdk";

interface Pokemon {
  id: number;
  name: string;
  type: string;
  image: string;
}

export default {
  data() {
    return {
      pokemons: [] as Pokemon[],
    };
  },
  mounted() {
    this.fetchPokemon();
  },
  methods: {
    async fetchPokemon() {

      // Init SDK
      const manifest = new Manifest();

      // Fetch Pokemons from the backend.
      manifest.from("pokemon")
        .find<Pokemon>()
        .then((res) => {
          // Store the response in the "pokemons" array
          this.pokemons = res;
        });
    },
  },
};
</script>

<template>
    <ul>
        <li v-for="pokemon of pokemons">{{ pokemon.name}}</li>
    </ul>
</template>


```

Checkout the [SDK doc](connect.md) to see more usages of the SDK.,
