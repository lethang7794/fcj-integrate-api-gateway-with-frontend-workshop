---
title: "Configure the frontend application with the Invoke URL"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

1. In the extracted source code of the frontend application.
2. Create a new `.env` file with the following content.

   ```
   VITE_API_GATEWAY_URL=https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE
   ```

   > [!NOTE]
   > Replace `https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE` with the Invoke URL you've just copied.

![alt text](/images/workshop-3/frontend-app--env.png)
