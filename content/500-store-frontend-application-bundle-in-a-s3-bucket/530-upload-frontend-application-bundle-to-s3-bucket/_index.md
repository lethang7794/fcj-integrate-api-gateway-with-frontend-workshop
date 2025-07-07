---
title: "Upload frontend application bundle to S3 bucket"
weight: 1
chapter: false
pre: " <b> 5.3 </b> "
---

## Open the Upload page

1. Open the detail page of your S3 bucket `fcj-hall-of-fame`.

2. In the `Object` tab - which is opened by default - click `Upload`.

![alt text](/images/workshop-3/s3--upload-objects.jpg)

## Select the files and folder to upload

### To add the `assets` folder

- Click `Add folder`

![alt text](/images/workshop-3/s3--upload-objects--add-folder.jpg)

- Select the `assets` folder in the `dist` folder (of your frontend application)
- Click `Upload`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-assets.png)

- Click `Upload` again to confirm upload all files from `assets`.

### To add the `images` folder

- Click `Add folder`

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images.png)

- Select the `images` folder in the `dist` folder (of your frontend application)
- Click `Upload`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-select.png)

- Click `Upload` again to confirm upload all files from `images`.

![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-confirm.png)

### To add the `index.html` file

- Click `Add files`

![alt text](/images/workshop-3/s3--upload-objects--upload-file-index.png)

- Select the `index.html` file in the `dist` folder (of your frontend application)
- Click `Open`.

![alt text](/images/workshop-3/s3--upload-objects--upload-file-index-confirm.png)

## Upload the files and folder

- After add these files and folder, scroll to bottom, click `Upload`

![alt text](/images/workshop-3/s3--upload-objects--upload--confirm.png)

- Wait for the files and folders to be uploaded to your S3 bucket.

![alt text](/images/workshop-3/s3--upload-objects--upload--progress.jpg)

- When the upload is finished, you will see an `Upload succeeded` notification.

- In the `Summary` section, click on the URI of the S3 bucket (`s3://fcj-hall-of-fame`) to go back to the detail page of the bucket.

![alt text](/images/workshop-3/s3--upload-objects--upload--status.jpg)
