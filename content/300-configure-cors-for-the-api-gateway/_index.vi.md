---
title: "Cấu hình CORS cho API Gateway"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

1. Mở [mục APIs](https://console.aws.amazon.com/apigateway/main/apis) trong bảng điều khiển API Gateway.
2. Trong danh sách các API, nhấp vào tên API (`UsersAPI`).

![alt text](/images/workshop-3/API-Gateway--list-APIs.png)

3. Bạn sẽ được chuyển hướng đến phần _Resources_ của `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.png)

> [!NOTE]
> Với API Gateway, cài đặt CORS được áp dụng ở cấp độ tài nguyên, vì vậy chúng ta cần cấu hình cài đặt CORS cho 2 tài nguyên (`/users` và `users/{usersId}`)
