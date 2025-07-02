---
title: "Configure CORS for /users/{userId} resource"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

- Go to the `Resources` section of the `UsersAPI`.
- Select the `/users/{userId}` resource.
- Click `Enable CORS`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--enable-CORS.png)

- In the `Enable CORS` page - `CORS Settings` section:

  - For `Access-Control-Allow-Methods`, select `GET`, `DELETE`, `POST`.
  - Click `Save`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--CORS-settings.png)

- Click `Details` in the `Successfully enabled CORS` notification, you will see that API Gateway has:

  - Created `OPTIONS` method ...
  - Added `Access-Control-Allow-Origin` to the `GET`/`DELETE`/`POST` method:

    - Method Response Header
    - Integration Response Header Mapping
