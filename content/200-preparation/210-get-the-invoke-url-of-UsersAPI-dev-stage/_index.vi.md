---
title: "Lấy Invoke URL của giai đoạn dev trong UsersAPI"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

Ứng dụng frontend sẽ tích hợp với REST API của bạn (được tạo bằng API Gateway) thông qua _Invoke URL_.

## Lấy Invoke URL của giai đoạn dev trong UsersAPI

1. Mở [mục APIs](https://console.aws.amazon.com/apigateway/main/apis) trong bảng điều khiển API Gateway.
2. Trong danh sách các API, nhấp vào tên API (`UsersAPI`).
3. Bạn sẽ được chuyển hướng đến phần _Resources_ của `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.jpg)

4. Chọn phần `Stages` của `UsersAPI`.
5. Chọn môi trường (stage) `dev`.
6. Trong phần `Stage details` - `Invoke URL`, nhấp vào biểu tượng sao chép để sao chép _Invoke URL_ của môi trường (stage) `dev` trong `UsersAPI`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--stages.jpg)
