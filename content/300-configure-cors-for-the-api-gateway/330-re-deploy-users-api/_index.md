---
title: "Re-deploy `UsersAPI`"
weight: 2
chapter: false
pre: " <b> 3.3. </b> "
---

After enable CORS for `/users` and `/users/{userId}` resources, you need to re-deploy the API so the new settings is applied in your `dev` stage.

1. Go to the `Resources` section of the `UsersAPI`.
2. Click `Deploy API`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--redeploy-button.png)

3. Choose the `dev` stage (that you've created).
4. Click `Deploy`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--redeploy-stage.png)
