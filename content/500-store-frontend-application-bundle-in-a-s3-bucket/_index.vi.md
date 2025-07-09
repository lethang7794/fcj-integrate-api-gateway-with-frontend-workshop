---
title: "Lưu trữ ứng dụng frontend trong một S3 bucket"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

Trong phần này, bạn sẽ học cách chuẩn bị và triển khai ứng dụng frontend lên Amazon S3 để lưu trữ trang web tĩnh. Quy trình bao gồm ba bước chính:

1. **Xây dựng Ứng dụng Frontend**: Biên dịch mã nguồn frontend thành các file tĩnh sẵn sàng cho môi trường production bằng lệnh build.
2. **Tạo S3 Bucket**: Thiết lập một S3 bucket mới trong AWS với cấu hình phù hợp để lưu trữ trang web tĩnh.
3. **Tải lên các File lên S3**: Tải lên các file frontend đã được build lên S3 bucket.

Đến cuối phần này, ứng dụng frontend của bạn sẽ được lưu trữ trong một S3 bucket trên AWS, sẵn sàng để phục vụ với tính năng lưu trữ trang web tĩnh của S3.
