---
title: "Tải gói ứng dụng frontend lên S3 bucket"
weight: 1
chapter: false
pre: " <b> 5.3 </b> "
---

## Mở trang Tải lên

1. Mở trang chi tiết S3 bucket `fcj-hall-of-fame` của bạn.

2. Trong tab `Object` (mở mặc định), nhấp vào `Upload` (Tải lên).

![alt text](/images/workshop-3/s3--upload-objects.jpg)

## Chọn tệp và thư mục để tải lên

### Để thêm thư mục `assets`

- Nhấp vào `Add folder`

![alt text](/images/workshop-3/s3--upload-objects--add-folder.jpg)

- Chọn thư mục `assets` trong thư mục `dist` (của ứng dụng frontend của bạn)
- Nhấp `Upload`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-assets.png)

- Nhấp `Upload` một lần nữa để xác nhận tải lên tất cả các tệp từ `assets`.

### Để thêm thư mục `images`

- Nhấp vào `Add folder`

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images.png)

- Chọn thư mục `images` trong thư mục `dist` (của ứng dụng frontend của bạn)
- Nhấp `Upload`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-select.png)

- Nhấp `Upload` một lần nữa để xác nhận tải lên tất cả các tệp từ `images`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-confirm.png)

### Để thêm tệp `index.html`

- Nhấp vào `Add files`

![alt text](/images/workshop-3/s3--upload-objects--upload-file-index.png)

- Chọn tệp `index.html` trong thư mục `dist` (của ứng dụng frontend của bạn)
- Nhấp `Open`.

![alt text](/images/workshop-3/s3--upload-objects--upload-file-index-confirm.png)

## Tải lên các tệp và thư mục

- Sau khi thêm các tệp và thư mục, cuộn xuống dưới cùng, nhấp vào `Upload`

![alt text](/images/workshop-3/s3--upload-objects--upload--confirm.png)

- Chờ các tệp và thư mục được tải lên S3 bucket của bạn.

![alt text](/images/workshop-3/s3--upload-objects--upload--progress.jpg)

- Khi quá trình tải lên hoàn tất, bạn sẽ thấy thông báo `Upload succeeded` (Tải lên thành công).

- Trong phần `Summary` (Tóm tắt), nhấp vào URI của S3 bucket (`s3://fcj-hall-of-fame`) để quay lại trang chi tiết của bucket.

![alt text](/images/workshop-3/s3--upload-objects--upload--status.jpg)
