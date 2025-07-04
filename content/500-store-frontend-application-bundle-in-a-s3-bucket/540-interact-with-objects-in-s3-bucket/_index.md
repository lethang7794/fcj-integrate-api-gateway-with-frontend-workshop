---
title: "Interact with objects in S3 bucket"
weight: 1
chapter: false
pre: " <b> 5.4 </b> "
---

- After upload the application bundle to `fcj-hall-of-fame` bucket, go back to the detail of the bucket, you will see the list of objects.

  ![alt text](/images/workshop-3/s3-bucket--list-objects.png)

- Click on the `index.html` object to see its detail.

  ![alt text](/images/workshop-3/s3-bucket--index-object.png)

- If you click on the `Object URL`, you will get an `Access Denied` response in XML.

  ![alt text](/images/workshop-3/s3-bucket--index-object--access-denied.png)

  > [!NOTE]
  > You can use the Object URL to access an object if: 1. The object allow _public access_ (it is shared with anyone in the Internet). 2. The bucket doesn't have `Block Public access` feature turned on.

  > [!NOTE]
  > By default, new buckets, and objects don't allow public access,

- But you've just uploaded the objects into your S3 bucket, you can access these objects directly using the S3 Management Console.

  - In the detail page of the `index.html` object, click on the `Open` button.
  - Your browser will open the object in a new tab.

    The URL will be a very long text:

    ```
    https://fcj-hall-of-fame.s3.ap-southeast-1.amazonaws.com/index.html?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIA6ELKN2NTE2GUFM23%2F20250520%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250520T072058Z&X-Amz-Expires=300&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEOf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhALHhmIRTNeQVzxdt46DNSG6PhzxAPXkWOxsY2Yl8MuDfAiBxBptuMIWEWq%2F4oaQ7SyNbmNhlmXnPOkerKWjXxRsNRiqEAwig%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDk3MTQyMjY4NDAwNiIMRV7cbqTeNTrP%2Bag3KtgCdFfSUXd%2BuwoauDHmSrH0RNex6UdJe4AJu9UdPCk2P6CYYk9bDbelggCWbppgEpptPIYMofVrZh2egPZaJzFskP29TGXf8TZRMOlmkFNVeR0jGJUDwotSt6Wsr5b7a4uOOrEjkf%2FStj76bmSfbQGoMo7SXb7XMg9y0MBnVt9bzDOSnK%2Ffh2ZDtLqGqFyCu5FILyQc3us8Uf7a08UdyVtyAbpa83ny4VunWzFtbg8u6gYGelec90al7GPi%2FW3mAZoGgy7R84BBvs4bghbkOJHwo6R6XLs3VFcN4fgvhcyau%2FzvYgV6gXLHDTgCs20YQ%2BRwkXRgnW93yByMCx5Bc2XrjTeS2DxY%2FnzHU1gD87rEASGl1aWIiWL6KYA0DXwCdJ5adThu8sEHSvZZwiup796PD%2BY3RB7%2F8cEAIUpt04TZrR%2BTqg6a6zlW%2Fw6hasKMTkVZhzh3Zm3pIH0w%2F8mwwQY6rQKZxfU4AqUuXORiayxgIFR7ZOhcivfhaFV1YwKsW%2F6AbCnCtEN1b5WR4XihWsL%2BssdbonPvM66MdmJVZT%2B0qX%2F3Sjwknwh3HUbbtaDa1SjaCFXOK%2FBgeSACrExKouRUR8gv7aY%2Fztkff64b5QKPx2b7dWcqbdN%2BEzW%2BbVsAyyPZ2YvpM0W8JqSMKXpeSOtKizuARJtPmZdHmRn9u5WIaiG47yhOXwyY4UjbR09bhsGzOV2bLGXAMGFOpbIPHK2PP32HRWSQt%2BfCX4upPx%2FShQ6oD%2BxKfxIcB1xNVee6MsVqV1m1GgBndCZQ0eWYQNTZrG4UUzYb8nDCgg2oyQ04l134n6C3a63qrcolTy%2FlyuTnpDFBdBTmcBtsV9Jxy6HPq9Bj5aJ8RO5vYSWoqKLO&X-Amz-Signature=d4ab2e53d32c8406298a7dd65a9c72736f0b6fc8fa53b48c2d0dbdfb135d3d54&X-Amz-SignedHeaders=host&response-content-disposition=inline
    ```

    It's

    - The same `Object URL` (`https://fcj-hall-of-fame.s3.ap-southeast-1.amazonaws.com/index.html`)
    - But with some additional query params:

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
> When you click the Open button: 1. S3 generates a pre-signed URL for the object. 2. You open the object via that pre-signed URL. For more information, see [Sharing objects with pre-signed URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html)
