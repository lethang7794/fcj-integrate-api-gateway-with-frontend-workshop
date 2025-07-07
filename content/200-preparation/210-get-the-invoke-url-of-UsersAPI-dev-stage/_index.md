---
title: "Get the Invoke URL of our UsersAPI's dev stage"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

The frontend app will integrate with your REST API (created with API Gateway) via the _Invoke URL_.

## Get the Invoke URL of our UsersAPI's dev stage

1. Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
2. In the list of the APIs, click on the name of the API (`UsersAPI`).
3. You will be redirected to the _Resources_ section of the `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.jpg)

4. Select the `Stages` section of the `UsersAPI`.
5. Select the `dev` stage.
6. In the `Stage details` section - `Invoke URL`, click the copy icon to copy the _Invoke URL_ of the `dev` stage of the `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--stages.jpg)
