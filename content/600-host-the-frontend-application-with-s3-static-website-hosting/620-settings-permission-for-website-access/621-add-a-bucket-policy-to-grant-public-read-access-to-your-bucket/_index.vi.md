---
title: "Thêm chính sách bucket để cấp quyền đọc công khai cho bucket của bạn"
weight: 1
chapter: false
pre: " <b> 6.2.1 </b> "
---

1. Trong trang chi tiết của S3 bucket, mở tab `Permissions` (Quyền).
2. Trong phần `Bucket policy` (Chính sách bucket), nhấp vào `Edit` (Chỉnh sửa).

![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access.png)

3. Trang `Edit bucket policy` (Chỉnh sửa chính sách bucket), điền vào trường `Policy` (Chính sách):

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::fcj-hall-of-fame/*"
       }
     ]
   }
   ```

> [!NOTE]
> Thay thế `arn:aws:s3:::fcj-hall-of-fame` bằng ARN của S3 bucket của bạn.

![alt text](/images/workshop-3/s3-bucket--permisions--bucket-policy--grant-public-access.png)

4. Cuộn xuống dưới cùng, nhấp vào `Save changes` (Lưu thay đổi).
