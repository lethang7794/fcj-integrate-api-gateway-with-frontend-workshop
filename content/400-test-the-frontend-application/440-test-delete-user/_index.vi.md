---
title: "Kiểm tra xóa người dùng"
weight: 4
chapter: false
pre: " <b> 4.4 </b> "
---

1. Quay lại ứng dụng frontend của bạn (tại <http://localhost:5173/>).
2. Trong danh sách người dùng, ở hàng của người dùng có tên `William Henry Gates III`, nhấp vào nút `Action` (ba dấu chấm ở cuối hàng).
3. Nhấp vào `Delete`.

![alt text](/images/workshop-3/frontend-app--test-delete-user.png)

4. Nhập email của người dùng đó `bill@microsoft.com` vào ô nhập liệu.
5. Nhấp vào Delete.

![alt text](/images/workshop-3/frontend-app--test-delete-user--confirm.png)

6. Bạn sẽ thấy người dùng đã xóa không còn tồn tại trong danh sách người dùng nữa.

![alt text](/images/workshop-3/frontend-app--test-create-user--user-deleted.png)

> [!NOTE]
> Bây giờ bạn có thể yên tâm rằng frontend hoạt động như mong đợi, nhưng nó vẫn đang chạy trên máy cục bộ của bạn tại <http://localhost:5173/>.
