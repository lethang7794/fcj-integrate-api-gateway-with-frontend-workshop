---
title: "Preparation"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

> [!IMPORTANT]
> You need to complete workshop 1 and workshop 2 of this series before continue with this workshop.

## Preparation

### Download source code and tools

- Download the source code of the frontend application from this link <!-- TODO: add link to source code  -->
- Extract the source code.
- The frontend app use [pnpm](https://pnpm.io/) as the package manager for Node.js, so you will need to install `pnpm`. Use this [official guide](https://pnpm.io/installation) to install `pnpm`.

### Configure the frontend application

The frontend app will integrate with your REST API (created with API Gateway) via the _Invoke URL_.

You need to:

- Copy the Invoke URL.

  - Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
  - In the list of the APIs, click on the name of the API (`UsersAPI`).
  - You will be redirected to the _Resources_ section of the `UsersAPI`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.jpg)

  - Select the `Stages` section of the `UsersAPI`.
  - Select the `dev` stage.
  - In the `Stage details` section - `Invoke URL`, click the copy icon to copy the _Invoke URL_ of the `dev` stage of the `UsersAPI`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--stages.jpg)

- Configure the frontend with the Invoke URL.

  - In the extracted source code of the frontend application.
  - Create a new `.env` file with the following content.

    ```
    VITE_API_GATEWAY_URL=https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE
    ```

    ![alt text](/images/workshop-3/frontend-app--env.png)

> [!NOTE]
> Replace `https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE` with the Invoke URL you've just copied.

### Start the frontend application

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
