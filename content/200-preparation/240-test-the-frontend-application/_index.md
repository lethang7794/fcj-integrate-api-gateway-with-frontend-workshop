---
title: "Test the frontend application"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

- Open the extracted source code in a Terminal.

- Install dependencies:

  ```shell
  pnpm install
  ```

- Start the frontend applications

  ```shell
  pnpm run dev
  ```

  ![alt text](/images/workshop-3/frontend-app--dev.png)

- Open the frontend application at <http://localhost:5173/> with your browser. You should see the following UI.

  ![alt text](/images/workshop-3/frontend-app--ui.png)

- Open the Inspect feature of your browser

  ![alt text](/images/workshop-3/frontend-app--inspect.png)

- Click of the `Console` tab, you should see some red text about `Access to fetch at 'https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE/users' from origin 'http://localhost:5173' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

  ![alt text](/images/workshop-3/frontend-app--cors-error.png)
