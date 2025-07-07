---
title: "Cleanup"
weight: 7
chapter: false
pre: "<b>7. </b>"
---

{{% toc %}}

---

In additional to the resources in:

- Workshop 1: DynamoDB, Lambda functions, IAM Roles.
- Workshop 2: API Gateway.

For this workshop, you need to clean up the following resources:

- The S3 bucket.

---

## Empty the bucket

1. Open [_General purpose buckets_ section](https://console.aws.amazon.com/s3/buckets) of the S3 console.
2. In the list of the bucket:

   - Select `fcj-hall-of-fame` bucket.
   - Click `Empty`.

   ![alt text](/images/workshop-3/clean-up--list-buckets.png)

3. In the `Empty bucket` page:

- Type in `permanently delete`.
- Click `Empty`.

![alt text](/images/workshop-3/clean-up--empty-bucket.png)

4. Wait still you receive a "Successfully emptied bucket" message.

![alt text](/images/workshop-3/clean-up--empty-bucket-succeed.png)

- Click `Exit` to return to the list of S3 buckets.

## Delete the bucket

In the list of the bucket:

- Select `fcj-hall-of-fame` bucket.
- Click `Delete`.

  ![alt text](/images/workshop-3/clean-up--delete-bucket.png)

- Type in the bucket name `fcj-hall-of-fame`
- Click `Delete bucket`.

  ![alt text](/images/workshop-3/clean-up--delete-bucket-confirm.png)
