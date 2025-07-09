---
title: "Cấu hình CORS cho tài nguyên /users/{userId}"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

1. Đi đến phần `Resources` của `UsersAPI`.
2. Chọn tài nguyên `/users/{userId}`.
3. Nhấp vào `Enable CORS`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--enable-CORS.png)

4. Trong trang `Enable CORS` - phần `CORS Settings`:

   - Tại `Access-Control-Allow-Methods`, chọn `GET`, `DELETE`, `POST`.
   - Nhấp vào `Save`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--CORS-settings.png)

5. Nhấp vào `Details` trong thông báo `Successfully enabled CORS`, bạn sẽ thấy API Gateway đã:

   - Tạo phương thức `OPTIONS` ...
   - Thêm `Access-Control-Allow-Origin` vào phương thức `GET`/`DELETE`/`POST`:

     - Method Response Header
     - Integration Response Header Mapping
