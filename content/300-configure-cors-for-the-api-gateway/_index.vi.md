---
title: "Configure CORS for the API Gateway"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

1. Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
2. In the list of the APIs, click on the name of the API (`UsersAPI`).

![alt text](/images/workshop-3/API-Gateway--list-APIs.png)

3. You will be redirected to the _Resources_ section of the `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.png)

> [!NOTE]
> With API Gateway, the CORS settings is applied at resource-level, so we need to configure CORS settings for two 2 resources (`/users` and `users/{usersId}`)
