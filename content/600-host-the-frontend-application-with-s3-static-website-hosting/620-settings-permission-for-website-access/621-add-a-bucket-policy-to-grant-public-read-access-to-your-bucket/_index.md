---
title: "Add a bucket policy to grant public read access to your bucket"
weight: 1
chapter: false
pre: " <b> 6.2.1 </b> "
---

- In the detail page of your S3 bucket, open `Permissions` tab.
- Under `Bucket policy` section, click `Edit`.

  ![alt text](/images/workshop-3/s3-bucket--permisions--block-public-access.png)

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
