---
title: "Cấu hình ứng dụng frontend với Invoke URL"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

1. Trong thư mục mã nguồn frontend đã giải nén.
2. Tạo một file `.env` mới với nội dung sau:

   ```
   VITE_API_GATEWAY_URL=https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE
   ```

   > [!NOTE]
   > Thay thế `https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE` bằng Invoke URL bạn vừa sao chép.

![alt text](/images/workshop-3/frontend-app--env.png)
