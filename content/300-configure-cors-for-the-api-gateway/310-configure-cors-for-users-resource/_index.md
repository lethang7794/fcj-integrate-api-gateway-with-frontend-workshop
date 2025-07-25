---
title: "Configure CORS for /users resource"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

1. Select the `/users` resource.
2. Click `Enable CORS`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS.png)

3. In the `Enable CORS` page - `CORS Settings` section:

   - For `Access-Control-Allow-Methods`, select `GET` and `POST`.
   - Click `Save`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--CORS-settings.png)

4. Click `Details` in the `Successfully enabled CORS` notification, you will see that API Gateway has:

   - Created `OPTIONS` method ...
   - Added `Access-Control-Allow-Origin` to the `GET`/`POST` method:

     - Method Response Header
     - Integration Response Header Mapping

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS-detail.png)
