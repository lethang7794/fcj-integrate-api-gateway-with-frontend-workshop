---
title: "Configure CORS for /users/{userId} resource"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

1. Go to the `Resources` section of the `UsersAPI`.
2. Select the `/users/{userId}` resource.
3. Click `Enable CORS`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--enable-CORS.png)

4. In the `Enable CORS` page - `CORS Settings` section:

   - For `Access-Control-Allow-Methods`, select `GET`, `DELETE`, `POST`.
   - Click `Save`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--CORS-settings.png)

5. Click `Details` in the `Successfully enabled CORS` notification, you will see that API Gateway has:

   - Created `OPTIONS` method ...
   - Added `Access-Control-Allow-Origin` to the `GET`/`DELETE`/`POST` method:

     - Method Response Header
     - Integration Response Header Mapping
