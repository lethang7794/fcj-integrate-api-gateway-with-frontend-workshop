---
title: "Tắt tính năng Chặn truy cập công khai S3"
weight: 2
chapter: false
pre: " <b> 6.2.2 </b> "
---

1. Trong trang chi tiết của S3 bucket, mở tab `Permissions` (Quyền).
2. Trong phần `Block public access (bucket settings)` (Chặn quyền truy cập công khai - cài đặt bucket), nhấp vào `Edit` (Chỉnh sửa).

![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access.png)

3. Trong trang `Edit Block public access (bucket settings)` (Chỉnh sửa chặn quyền truy cập công khai - cài đặt bucket):

   - Bỏ chọn tất cả các ô kiểm.
   - Nhấp vào `Save changes` (Lưu thay đổi).

![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access--edit.png)

4. Trong cửa sổ bật lên `Edit Block public access (bucket settings)` (Chỉnh sửa chặn quyền truy cập công khai - cài đặt bucket):

   - Nhập `confirm`.
   - Nhấp vào `Confirm` (Xác nhận).

![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access--confirm.png)

> [!IMPORTANT]
> S3 Block Public Access là một lớp bảo vệ bổ sung (ở cấp độ bucket) để ngăn chặn việc bất kỳ S3 bucket nào bị công khai ra internet (thông qua chính sách bucket).

---

5. Bây giờ bạn có thể truy cập ứng dụng frontend của mình thông qua điểm cuối trang web của bucket.

![alt text](/images/workshop-3/s3-bucket--static-website-hosting--frontend-app.png)
