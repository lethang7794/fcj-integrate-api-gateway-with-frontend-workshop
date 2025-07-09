---
title: "Tương tác với các đối tượng trong S3 bucket"
weight: 1
chapter: false
pre: " <b> 5.4 </b> "
---

1. Sau khi tải lên gói ứng dụng lên bucket `fcj-hall-of-fame`, quay lại trang chi tiết của bucket, bạn sẽ thấy danh sách các đối tượng.

![alt text](/images/workshop-3/s3-bucket--list-objects.png)

2. Nhấp vào đối tượng `index.html` để xem chi tiết.

![alt text](/images/workshop-3/s3-bucket--index-object.png)

3. Nếu bạn nhấp vào `Object URL`, bạn sẽ nhận được phản hồi `Access Denied` dưới dạng XML.

![alt text](/images/workshop-3/s3-bucket--index-object--access-denied.png)

> [!NOTE]
> Bạn có thể sử dụng Object URL để truy cập một đối tượng nếu: 1. Đối tượng cho phép _truy cập công khai_ (được chia sẻ với bất kỳ ai trên Internet). 2. Bucket không bật tính năng `Block Public access`.

> [!TIP]
> Theo mặc định, các bucket và đối tượng mới không cho phép truy cập công khai.

4. Nhưng vì bạn vừa tải lên các đối tượng vào S3 bucket của mình, bạn có thể truy cập trực tiếp các đối tượng này bằng S3 Management Console.

- Trang chi tiết của đối tượng `index.html`, nhấp vào nút `Open`.
- Trình duyệt của bạn sẽ mở đối tượng trong một tab mới.

  URL sẽ là một đoạn văn bản rất dài:

  ```
  https://fcj-hall-of-fame.s3.ap-southeast-1.amazonaws.com/index.html?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIA6ELKN2NTE2GUFM23%2F20250520%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250520T072058Z&X-Amz-Expires=300&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEOf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhALHhmIRTNeQVzxdt46DNSG6PhzxAPXkWOxsY2Yl8MuDfAiBxBptuMIWEWq%2F4oaQ7SyNbmNhlmXnPOkerKWjXxRsNRiqEAwig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDk3MTQyMjY4NDAwNiIMRV7cbqTeNTrP%2Bag3KtgCdFfSUXd%2BuwoauDHmSrH0RNex6UdJe4AJu9UdPCk2P6CYYk9bDbelggCWbppgEpptPIYMofVrZh2egPZaJzFskP29TGXf8TZRMOlmkFNVeR0jGJUDwotSt6Wsr5b7a4uOOrEjkf%2FStj76bmSfbQGoMo7SXb7XMg9y0MBnVt9bzDOSnK%2Ffh2ZDtLqGqFyCu5FILyQc3us8Uf7a08UdyVtyAbpa83ny4VunWzFtbg8u6gYGelec90al7GPi%2FW3mAZoGgy7R84BBvs4bghbkOJHwo6R6XLs3VFcN4fgvhcyau%2FzvYgV6gXLHDTgCs20YQ%2BRwkXRgnW93yByMCx5Bc2XrjTeS2DxY%2FnzHU1gD87rEASGl1aWIiWL6KYA0DXwCdJ5adThu8sEHSvZZwiup796PD%2BY3RB7%2F8cEAIUpt04TZrR%2BTqg6a6zlW%2Fw6hasKMTkVZhzh3Zm3pIH0w%2F8mwwQY6rQKZxfU4AqUuXORiayxgIFR7ZOhcivfhaFV1YwKsW%2F6AbCnCtEN1b5WR4XihWsL%2BssdbonPvM66MdmJVZT%2B0qX%2F3Sjwknwh3HUbbtaDa1SjaCFXOK%2FBgeSACrExKouRUR8gv7aY%2Fztkff64b5QKPx2b7dWcqbdN%2BEzW%2BbVsAyyPZ2YvpM0W8JqSMKXpeSOtKizuARJtPmZdHmRn9u5WIaiG47yhOXwyY4UjbR09bhsGzOV2bLGXAMGFOpbIPHK2PP32HRWSQt%2BfCX4upPx%2FShQ6oD%2BxKfxIcB1xNVee6MsVqV1m1GgBndCZQ0eWYQNTZrG4UUzYb8nDCgg2oyQ04l134n6C3a63qrcolTy%2FlyuTnpDFBdBTmcBtsV9Jxy6HPq9Bj5aJ8RO5vYSWoqKLO&X-Amz-Signature=d4ab2e53d32c8406298a7dd65a9c72736f0b6fc8fa53b48c2d0dbdfb135d3d54&X-Amz-SignedHeaders=host&response-content-disposition=inline
  ```

  Đó là:

  - Cùng một `Object URL` (`https://fcj-hall-of-fame.s3.ap-southeast-1.amazonaws.com/index.html`)
  - Nhưng có thêm một số tham số truy vấn:

    ```
    X-Amz-Algorithm=AWS4-HMAC-SHA256
    X-Amz-Content-Sha256=UNSIGNED-PAYLOAD
    X-Amz-Credential=ASIA6ELKN2NTE2GUFM23%2F20250520%2Fap-southeast-1%2Fs3%2Faws4_request
    X-Amz-Date=20250520T072058Z
    X-Amz-Expires=300
    X-Amz-Security-Token=IQoJb3JpZ2luX2VjEOf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhALHhmIRTNeQVzxdt46DNSG6PhzxAPXkWOxsY2Yl8MuDfAiBxBptuMIWEWq%2F4oaQ7SyNbmNhlmXnPOkerKWjXxRsNRiqEAwig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDk3MTQyMjY4NDAwNiIMRV7cbqTeNTrP%2Bag3KtgCdFfSUXd%2BuwoauDHmSrH0RNex6UdJe4AJu9UdPCk2P6CYYk9bDbelggCWbppgEpptPIYMofVrZh2egPZaJzFskP29TGXf8TZRMOlmkFNVeR0jGJUDwotSt6Wsr5b7a4uOOrEjkf%2FStj76bmSfbQGoMo7SXb7XMg9y0MBnVt9bzDOSnK%2Ffh2ZDtLqGqFyCu5FILyQc3us8Uf7a08UdyVtyAbpa83ny4VunWzFtbg8u6gYGelec90al7GPi%2FW3mAZoGgy7R84BBvs4bghbkOJHwo6R6XLs3VFcN4fgvhcyau%2FzvYgV6gXLHDTgCs20YQ%2BRwkXRgnW93yByMCx5Bc2XrjTeS2DxY%2FnzHU1gD87rEASGl1aWIiWL6KYA0DXwCdJ5adThu8sEHSvZZwiup796PD%2BY3RB7%2F8cEAIUpt04TZrR%2BTqg6a6zlW%2Fw6hasKMTkVZhzh3Zm3pIH0w%2F8mwwQY6rQKZxfU4AqUuXORiayxgIFR7ZOhcivfhaFV1YwKsW%2F6AbCnCtEN1b5WR4XihWsL%2BssdbonPvM66MdmJVZT%2B0qX%2F3Sjwknwh3HUbbtaDa1SjaCFXOK%2FBgeSACrExKouRUR8gv7aY%2Fztkff64b5QKPx2b7dWcqbdN%2BEzW%2BbVsAyyPZ2YvpM0W8JqSMKXpeSOtKizuARJtPmZdHmRn9u5WIaiG47yhOXwyY4UjbR09bhsGzOV2bLGXAMGFOpbIPHK2PP32HRWSQt%2BfCX4upPx%2FShQ6oD%2BxKfxIcB1xNVee6MsVqV1m1GgBndCZQ0eWYQNTZrG4UUzYb8nDCgg2oyQ04l134n6C3a63qrcolTy%2FlyuTnpDFBdBTmcBtsV9Jxy6HPq9Bj5aJ8RO5vYSWoqKLO
    X-Amz-Signature=d4ab2e53d32c8406298a7dd65a9c72736f0b6fc8fa53b48c2d0dbdfb135d3d54&X-Amz-SignedHeaders=host&response-content-disposition=inline
    ```

> [!NOTE]
> Khi bạn nhấp vào nút Open: 1. S3 tạo ra một URL được ký trước cho đối tượng. 2. Bạn mở đối tượng thông qua URL được ký trước đó. Để biết thêm thông tin, xem [Chia sẻ đối tượng với URL được ký trước](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html)
