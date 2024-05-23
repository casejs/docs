---
id: install
---

# Install

## Prerequisites

- [NodeJS](https://nodejs.org/en/) (**18.x**).
- ⚠ A computer that runs Linux or macOS (Windows compatibility on the way !)

## Install Manifest

Run the following on your terminal:

```bash
npx add-manifest
```

This will create a `manifest/backend.yml` file and add the required dependencies.

Then serve the backend locally:

```
npm run manifest
```

You can now:
<br/> - See your **Admin panel** at http://localhost:1111 using the email `admin@manifest.build` and the password `manifest`
<br/> - Use your **REST API** at http://localhost:1111/api

:::tip

If you already have a frontend app, you can run the `add-manifest` command from your **project root** to include it in your repo.

:::
