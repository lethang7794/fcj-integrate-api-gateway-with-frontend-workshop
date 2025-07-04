---
title: "Turn off S3 Block Public Access"
weight: 2
chapter: false
pre: " <b> 6.2.2 </b> "
---

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

> [!IMPORTANT]
> S3 Block Public Access is another layer of protection (at the bucket level) to prevent any S3 bucket is publicly exposed to the internet (by the bucket policy).

---

- Now you can access your frontend application via the bucket website endpoint.

  ![alt text](/images/workshop-3/s3-bucket--static-website-hosting--frontend-app.png)
