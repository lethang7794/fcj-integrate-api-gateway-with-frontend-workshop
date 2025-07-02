---
title: Workshop 3
weight: 11
---

# Integrate API Gateway with frontend application hosted in S3

## Preparation

## Configure CORS for the API Gateway

### Configure CORS for `/users` resource

### Configure CORS for `/users/{userId}` resource

### Re-deploy `UsersAPI`

## Test the frontend application

### Test create new user

### Test list users

### Test update user

### Test delete user

## Store frontend application bundle in a S3 bucket

### Build your frontend application

### Create a S3 bucket

### Upload frontend application bundle to S3 bucket

### Interact with objects in S3 bucket

## Host the frontend application with S3 static website hosting

In this step, you will use S3 _static website hosting_ feature to

- Deploy your frontend application
- Expose it to people all over the world.

> [!NOTE]
> Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance.
>
> - Amazon S3 is built to store and retrieve any amount of data from anywhere.
> - You can use Amazon S3 to host a static website. On a static website, individual webpages include static content. They might also contain client-side scripts.
>
> See [Hosting a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)

### Turn on S3 static website hosting

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

> [!NOTE]
> Although you've turned on `Static website hosting` and had a `Bucket website endpoint`, you still can't publicly access the content of your website.
>
> If you want your website to be public, you must make all your content publicly readable for your customers to be able to access it at the website endpoint.
>
> In the next step, you will make your bucket publicly readable, so your website can be publicly access.

### Settings permission for website access

#### Turn off S3 Block Public Access

- In the detail page of your S3 bucket, open `Permissions` tab.
- Under `Block public access (bucket settings)` section, click `Edit`.

  ![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access.png)

- In the `Edit Block public access (bucket settings) page`:

  - Deselect all the checkboxes.
  - Click Save changes.

    ![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access--edit.png)

- In the `Edit Block public access (bucket settings)` popup,

  - Type `confirm`.
  - Click `Confirm`.

    ![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access--confirm.png)

#### Add a bucket policy to grant public read access to your bucket

- In the detail page of your S3 bucket, open `Permissions` tab.
- Under `Bucket policy` section, click `Edit`.

  ![alt text](/images/workshop-3/s3-bucket--permisions--bucket-policy.png)

- In the `Edit bucket policy` page, fill in the `Policy`:

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
  > Replace `arn:aws:s3:::fcj-hall-of-fame` with the ARN of your S3 bucket.

  ![alt text](/images/workshop-3/s3-bucket--permisions--bucket-policy--grant-public-access.png)

- Scroll to the bottom, click `Save changes`.

---

- Now you can access your frontend application via the bucket website endpoint.

  ![alt text](/images/workshop-3/s3-bucket--static-website-hosting--frontend-app.png)

## Clean up

In additional to the resources in:

- Workshop 1: DynamoDB, Lambda functions, IAM Roles.
- Workshop 2: API Gateway.

For this workshop, you need to clean up the following resources:

- The S3 bucket.

---

1. Open [_General purpose buckets_ section](https://console.aws.amazon.com/s3/buckets) of the S3 console.
2. In the list of the bucket:

   - Select `fcj-hall-of-fame` bucket.
   - Click `Empty`.

   ![alt text](/images/workshop-3/clean-up--list-buckets.png)

3. In the `Empty bucket` page:

   - Type in `permanently delete`.
   - Click `Empty`.

     ![alt text](/images/workshop-3/clean-up--empty-bucket.png)

   - Wait still you receive a "Successfully emptied bucket" message.

     ![alt text](/images/workshop-3/clean-up--empty-bucket-succeed.png)

   - Click `Exit` to return to the list of S3 buckets.

4. In the list of the bucket:

   - Select `fcj-hall-of-fame` bucket.
   - Click `Delete`.

     ![alt text](/images/workshop-3/clean-up--delete-bucket.png)

   - Type in the bucket name `fcj-hall-of-fame`
   - Click `Delete bucket`.

     ![alt text](/images/workshop-3/clean-up--delete-bucket-confirm.png)
