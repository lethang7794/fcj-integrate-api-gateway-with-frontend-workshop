---
title: "Kiểm tra ứng dụng frontend"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

1. Mở thư mục mã nguồn đã giải nén trong Terminal.

2. Cài đặt các phụ thuộc:

   ```shell
   pnpm install
   ```

3. Khởi động ứng dụng frontend:

   ```shell
   pnpm run dev
   ```

![alt text](/images/workshop-3/frontend-app--dev.png)

4. Mở ứng dụng frontend tại <http://localhost:5173/> bằng trình duyệt của bạn. Bạn sẽ thấy giao diện người dùng như sau:

![alt text](/images/workshop-3/frontend-app--ui.png)

5. Mở tính năng Kiểm tra (Inspect) của trình duyệt

![alt text](/images/workshop-3/frontend-app--inspect.png)

6. Nhấp vào tab `Console`, bạn sẽ thấy một số lỗi:

   ```
   Access to fetch at 'https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE/users' from origin 'http://localhost:5173' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
   ```

![alt text](/images/workshop-3/frontend-app--cors-error.png)

> [!CAUTION]
> Ứng dụng frontend của chúng ta đã gọi API Gateway, nhưng yêu cầu đã bị chặn bởi trình duyệt do cấu hình CORS của API Gateway.
