---
title: "Get the Invoke URL of our UsersAPI's dev stage"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

The frontend app will integrate with your REST API (created with API Gateway) via the _Invoke URL_.

## Get the Invoke URL of our UsersAPI's dev stage

- Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
- In the list of the APIs, click on the name of the API (`UsersAPI`).
- You will be redirected to the _Resources_ section of the `UsersAPI`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.jpg)

- Select the `Stages` section of the `UsersAPI`.
- Select the `dev` stage.
- In the `Stage details` section - `Invoke URL`, click the copy icon to copy the _Invoke URL_ of the `dev` stage of the `UsersAPI`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--stages.jpg)
