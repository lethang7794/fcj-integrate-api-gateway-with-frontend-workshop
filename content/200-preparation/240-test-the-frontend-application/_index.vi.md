---
title: "Test the frontend application"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

1. Open the extracted source code in a Terminal.

2. Install dependencies:

   ```shell
   pnpm install
   ```

3. Start the frontend applications

   ```shell
   pnpm run dev
   ```

![alt text](/images/workshop-3/frontend-app--dev.png)

4. Open the frontend application at <http://localhost:5173/> with your browser. You should see the following UI.

![alt text](/images/workshop-3/frontend-app--ui.png)

5. Open the Inspect feature of your browser

![alt text](/images/workshop-3/frontend-app--inspect.png)

6. Click of the `Console` tab, you should see some errors:

   ```
   Access to fetch at 'https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE/users' from origin 'http://localhost:5173' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
   ```

![alt text](/images/workshop-3/frontend-app--cors-error.png)

> [!CAUTION]
> Our frontend application has called the API Gateway, but the request is blocked by the browser because of the CORS settings of the API Gateway.
