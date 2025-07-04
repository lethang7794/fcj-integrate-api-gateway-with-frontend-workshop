---
title: "Turn on S3 static website hosting"
weight: 1
chapter: false
pre: " <b> 6.1 </b> "
---

In the detail page of your S3 bucket,

- Open `Properties` tab.

  ![alt text](/images/workshop-3/s3-bucket--properties.jpg)

- In the `Static website hosting` section, click `Edit`.

  ![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--edit.jpg)

- By default `Static website hosting` is `Disable`.

  ![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--disable.jpg)

- For `Static website hosting`, select `Enable`
- For `Hosting type`, select `Host a static website`.
- For `Index document`, enter `index.html`

  ![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--index-document.jpg)

- Scroll to bottom, click `Save changes`.

- You will be redirected back to the detail page of S3 bucket.
- Scroll to `Static website hosting` section, click the `Copy` button to copy the `Bucket website endpoint`.

  ![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--bucket-website-endpoint.jpg)

- Now let's open your website using the bucket website endpoint.

  ![alt text](/images/workshop-3/s3-bucket--properties--static-website-hosting--403.png)

  - It's a different error.
  - Now instead of receiving an `AccessDenied` response in XML, you receive an `403 Forbidden` response in HTML.

---

> [!TIP]
> Although you've turned on `Static website hosting` and had a `Bucket website endpoint`, you still can't publicly access the content of your website.
> If you want your website to be public, you must make all your content publicly readable for your customers to be able to access it at the website endpoint.

> [!NOTE]
> In the next step, you will make your bucket publicly readable, so your website can be publicly access.
