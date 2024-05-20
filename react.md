---
id: react
---

# Quick start with React

Give a proper backend to your React app.

:::warning

This quick start guide focuses exclusively on the **frontend**. To ensure the functionality of this code, your Manifest backend must be [up and running](install.md) at `http://localhost:1111`.

:::

# 1. Create a React app

If you already have a React app, you can skip this step.

There is several ways to do that. We will use the easiest one: **create-react-app**. You can replace `my-client` by the name of your front-end app.

```
npx create-react-app my-client
cd my-client
npm start
```

# 2. Install CASE SDK

Install the JS SDK from the root of your React app.

```
npm i @manifest/sdk
```

# 3. Use it in your app

In that example we are using a Pokemon entity [created previously](entities.md). Replace it by your own entity. This example uses TypeScript, you can remove the typing to have plain JS.

```js
// App.tsx
import Manifest from '@manifest/sdk';
import { useEffect, useState } from "react";

function App() {
  interface Pokemon {
    id: number;
    name: string;
  }

  const [pokemons, setPokemon] = useState<Pokemon[]>([]);

  useEffect(() => {
    // Init SDK.
    const manifest = new Manifest();

    // Fetch the list of Pokemons.
    manifest.from("pokemon")
      .find<Pokemon>()
      .then((res) => {
        setPokemon(res);
      });
  }, []);

  // Display a list of Pokemons.
  return (
    <ul>
      {pokemons.map((pokemon) => (
        <li>{pokemon.name}</li>
      ))}
    </ul>
  );
}

export default App;
```

Checkout the [SDK doc](connect.md) to see more usages of the SDK: CRUD operations, file upload, authentication,
