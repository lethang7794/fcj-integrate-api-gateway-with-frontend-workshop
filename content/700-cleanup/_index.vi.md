---
title: "Dọn dẹp tài nguyên"
weight: 7
chapter: false
pre: "<b>7. </b>"
---

{{% toc %}}

---

Ngoài các tài nguyên trong:

- Workshop 1: DynamoDB, hàm Lambda, Vai trò IAM.
- Workshop 2: API Gateway.

Đối với workshop này, bạn cần dọn dẹp các tài nguyên sau:

- S3 bucket.

---

## Làm trống bucket

1. Mở phần [_General purpose buckets_](https://console.aws.amazon.com/s3/buckets) trong bảng điều khiển S3.
2. Trong danh sách bucket:

   - Chọn bucket `fcj-hall-of-fame`.
   - Nhấp vào `Empty` (Làm trống).

   ![alt text](/images/workshop-3/clean-up--list-buckets.png)

3. Trang `Empty bucket` (Làm trống bucket):

- Nhập `permanently delete` (xóa vĩnh viễn).
- Nhấp vào `Empty` (Làm trống).

![alt text](/images/workshop-3/clean-up--empty-bucket.png)

4. Chờ cho đến khi bạn nhận được thông báo "Successfully emptied bucket" (Đã làm trống bucket thành công).

![alt text](/images/workshop-3/clean-up--empty-bucket-succeed.png)

- Nhấp vào `Exit` (Thoát) để quay lại danh sách bucket S3.

## Xóa bucket

Trong danh sách bucket:

- Chọn bucket `fcj-hall-of-fame`.
- Nhấp vào `Delete` (Xóa).

  ![alt text](/images/workshop-3/clean-up--delete-bucket.png)

- Nhập tên bucket `fcj-hall-of-fame`
- Nhấp vào `Delete bucket` (Xóa bucket).

  ![alt text](/images/workshop-3/clean-up--delete-bucket-confirm.png)
