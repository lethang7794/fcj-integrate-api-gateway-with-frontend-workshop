---
title: "Bật tính năng lưu trữ trang web tĩnh S3"
weight: 1
chapter: false
pre: " <b> 6.1 </b> "
---

Trong trang chi tiết của S3 bucket của bạn:

1. Mở tab `Properties` (Thuộc tính).

![alt text](/images/workshop-3/s3-bucket--properties.jpg)

2. Trong phần `Static website hosting`, nhấp vào `Edit` (Chỉnh sửa).

![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--edit.jpg)

3. Theo mặc định, `Static website hosting` đang ở trạng thái `Disable` (Tắt).

![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--disable.jpg)

4. Đối với `Static website hosting`, chọn `Enable` (Bật).
5. Đối với `Hosting type`, chọn `Host a static website` (Lưu trữ trang web tĩnh).
6. Đối với `Index document`, nhập `index.html`.

![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--index-document.jpg)

7. Cuộn xuống dưới cùng và nhấp vào `Save changes` (Lưu thay đổi).

8. Bạn sẽ được chuyển hướng trở lại trang chi tiết của S3 bucket.
9. Cuộn đến phần `Static website hosting`, nhấp vào nút `Copy` để sao chép `Bucket website endpoint` (Điểm cuối trang web của bucket).

![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--bucket-website-endpoint.jpg)

10. Bây giờ hãy mở trang web của bạn bằng cách sử dụng điểm cuối trang web của bucket.

![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--403.png)

- Đây là một lỗi khác.
- Thay vì nhận được phản hồi `AccessDenied` dạng XML, bây giờ bạn nhận được phản hồi `403 Forbidden` dạng HTML.

---

> [!TIP]
> Mặc dù bạn đã bật `Static website hosting` và có `Bucket website endpoint`, bạn vẫn chưa thể truy cập công khai nội dung trang web của mình.
> Nếu bạn muốn trang web của mình công khai, bạn phải đặt tất cả nội dung của mình ở chế độ đọc công khai để khách hàng có thể truy cập tại điểm cuối trang web.

> [!NOTE]
> Trong bước tiếp theo, bạn sẽ đặt quyền đọc công khai cho bucket của mình để trang web có thể được truy cập công khai.
