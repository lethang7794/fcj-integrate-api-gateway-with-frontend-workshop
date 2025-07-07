---
title: "Build your frontend application"
weight: 1
chapter: false
pre: " <b> 5.3 </b> "
---

## Build frontend application

1. First, we need to build the frontend application for production by running:

   ```shell
   pnpm run build
   ```

2. This will run `vite build` that produces an application bundle that is suitable to be served over a static hosting service.

3. Check the application bundle at `dist`

   ```shell
   $ tree dist
   dist
   ├── assets
   │   ├── 401-BBhoy51U.js
   │   ├── 403-pH7gA2BX.js
   │   ├── 404-CUltoGn3.js
   │   ├── 500-BEjnOsrW.js
   │   ├── 503-Dw-MojSM.js
   │   └── ...
   ├── images
   │   ├── favicon_light.png
   │   ├── favicon_light.svg
   │   ├── favicon.png
   │   ├── favicon.svg
   │   └── shadcn-admin.png
   └── index.html

   3 directories, 69 files
   ```

## Serve frontend application on your local network

You can use a file server to serve the application bundle (the `dist` directory) yourself.

For example, you can use [`vercel/serve`](https://github.com/vercel/serve) by running `pnpx server dist`.

Now, anyone in your local network (same Wifi, LAN) can access your application.

{{<figure src="/images/workshop-3/frontend-app--serve-in-local-network.png" title="" width=300pc >}}
