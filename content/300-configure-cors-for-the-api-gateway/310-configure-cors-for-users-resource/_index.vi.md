---
title: "Cấu hình CORS cho tài nguyên /users"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

1. Chọn tài nguyên `/users`.
2. Nhấp vào `Enable CORS`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS.png)

3. Trong trang `Enable CORS` - phần `CORS Settings`:

   - Tại `Access-Control-Allow-Methods`, chọn `GET` và `POST`.
   - Nhấp vào `Save`.

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--CORS-settings.png)

4. Nhấp vào `Details` trong thông báo `Successfully enabled CORS`, bạn sẽ thấy API Gateway đã:

   - Tạo phương thức `OPTIONS` ...
   - Thêm `Access-Control-Allow-Origin` vào phương thức `GET`/`POST`:

     - Method Response Header
     - Integration Response Header Mapping

![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS-detail.png)
