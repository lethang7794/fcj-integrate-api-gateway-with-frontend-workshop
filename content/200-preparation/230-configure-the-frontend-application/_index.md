---
title: "Configure the frontend application"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

## Configure the frontend with the Invoke URL

- In the extracted source code of the frontend application.
- Create a new `.env` file with the following content.

  ```
  VITE_API_GATEWAY_URL=https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE
  ```

  ![alt text](/images/workshop-3/frontend-app--env.png)

> [!NOTE]
> Replace `https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE` with the Invoke URL you've just copied.
