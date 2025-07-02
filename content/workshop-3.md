---
title: Workshop 3
weight: 11
---

# Integrate API Gateway with frontend application hosted in S3

In previous workshops, you have:

- Created Lambda functions and invoked them directly via function URLs.
- Created an REST API using API Gateway that backed by these Lambda functions; then invoke your REST API with `curl` (a web client that supports HTTPS).

In this workshop, you will:

- Integrate a frontend application (written in React) with your REST API.

  - Configure the application
  - Configure CORS for the API Gateway to allow communication from the frontend application.

- Deploy your frontend application using S3 _static website hosting_ feature.

## Preparation

> [!IMPORTANT]
> You need to complete workshop 1 and workshop 2 of this series before continue with this workshop.

### Download source code and tools

- Download the source code of the frontend application from this link <!-- TODO: add link to source code  -->
- Extract the source code.
- The frontend app use [pnpm](https://pnpm.io/) as the package manager for Node.js, so you will need to install `pnpm`. Use this [official guide](https://pnpm.io/installation) to install `pnpm`.

### Configure the frontend application

The frontend app will integrate with your REST API (created with API Gateway) via the _Invoke URL_.

You need to:

- Copy the Invoke URL.

  - Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
  - In the list of the APIs, click on the name of the API (`UsersAPI`).
  - You will be redirected to the _Resources_ section of the `UsersAPI`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.jpg)

  - Select the `Stages` section of the `UsersAPI`.
  - Select the `dev` stage.
  - In the `Stage details` section - `Invoke URL`, click the copy icon to copy the _Invoke URL_ of the `dev` stage of the `UsersAPI`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--stages.jpg)

- Configure the frontend with the Invoke URL.

  - In the extracted source code of the frontend application.
  - Create a new `.env` file with the following content.

    ```
    VITE_API_GATEWAY_URL=https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE
    ```

    ![alt text](/images/workshop-3/frontend-app--env.png)

> [!NOTE]
> Replace `https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE` with the Invoke URL you've just copied.

### Start the frontend application

- Open the extracted source code in a Terminal.

- Install dependencies:

  ```shell
  pnpm install
  ```

- Start the frontend applications

  ```shell
  pnpm run dev
  ```

  ![alt text](/images/workshop-3/frontend-app--dev.png)

- Open the frontend application at <http://localhost:5173/> with your browser. You should see the following UI.

  ![alt text](/images/workshop-3/frontend-app--ui.png)

- Open the Inspect feature of your browser

  ![alt text](/images/workshop-3/frontend-app--inspect.png)

- Click of the `Console` tab, you should see some red text about `Access to fetch at 'https://XXXXXXXXXX.execute-api.REGION.amazonaws.com/STAGE/users' from origin 'http://localhost:5173' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

  ![alt text](/images/workshop-3/frontend-app--cors-error.png)

## Configure CORS for the API Gateway

- Open [APIs section](https://console.aws.amazon.com/apigateway/main/apis) of the API Gateway console.
- In the list of the APIs, click on the name of the API (`UsersAPI`).

  ![alt text](/images/workshop-3/API-Gateway--list-APIs.png)

- You will be redirected to the _Resources_ section of the `UsersAPI`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--resources.png)

### Configure CORS for `/users` resource

- Select the `/users` resource.
- Click `Enable CORS`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS.png)

- In the `Enable CORS` page - `CORS Settings` section:

  - For `Access-Control-Allow-Methods`, select `GET` and `POST`.
  - Click `Save`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--CORS-settings.png)

- Click `Details` in the `Successfully enabled CORS` notification, you will see that API Gateway has:

  - Created `OPTIONS` method ...
  - Added `Access-Control-Allow-Origin` to the `GET`/`POST` method:

    - Method Response Header
    - Integration Response Header Mapping

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users--enable-CORS-detail.png)

### Configure CORS for `/users/{userId}` resource

- Go to the `Resources` section of the `UsersAPI`.
- Select the `/users/{userId}` resource.
- Click `Enable CORS`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--enable-CORS.png)

- In the `Enable CORS` page - `CORS Settings` section:

  - For `Access-Control-Allow-Methods`, select `GET`, `DELETE`, `POST`.
  - Click `Save`.

    ![alt text](/images/workshop-3/API-Gateway--UsersAPI--users-userId--CORS-settings.png)

- Click `Details` in the `Successfully enabled CORS` notification, you will see that API Gateway has:

  - Created `OPTIONS` method ...
  - Added `Access-Control-Allow-Origin` to the `GET`/`DELETE`/`POST` method:

    - Method Response Header
    - Integration Response Header Mapping

### Re-deploy API Gateway

After enable CORS for `/users` and `/users/{userId}` resources, you need to re-deploy the API so the new settings is applied in your `dev` stage.

- Go to the `Resources` section of the `UsersAPI`.
- Click `Deploy API`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--redeploy-button.png)

- Choose the `dev` stage (that you've created).
- Click `Deploy`.

  ![alt text](/images/workshop-3/API-Gateway--UsersAPI--redeploy-stage.png)

## Test the frontend application

- Now you can go back to your frontend application at <http://localhost:5173/>.

- Open `Inspect`, in `Console` tab, verify that there is no error about CORS.

  ![alt text](/images/workshop-3/frontend-app--no-CORS-error.png)

- Now you can test your frontend application.

### Test create new user

- Create a user with name of `Bill Gates` and email of `bill@gates.com`.

  - Click `Add user`.

    ![alt text](/images/workshop-3/frontend-app--test-create-user.png)

  - Enter:

    - `Name`: `Bill Gates`
    - `Email`: `bill@gates.com`

  - Click `Create`

    ![alt text](/images/workshop-3/frontend-app--test-create-user--confirm.png)

  - You should see the new user in the list.

    ![alt text](/images/workshop-3/frontend-app--test-create-user--user-created.png)

- Repeat this step to create 2 other users:

  - A user with name of `Steve Jobs` and email of `steve@jobs.com`.
  - A user with name of `Jeff Bezos` and email of `jeff@bezos.com`.

- You should see 3 users in the list.

  ![alt text](/images/workshop-3/frontend-app--test-create-user--three-users-created.png)

### Test list users

- In the previous step, you've just created 3 users.
- Go back to your frontend application (at <http://localhost:5173/>).
- Refresh the page (press `F5` or click `Refresh` button) and verify that these 3 users are still showing.

  ![alt text](/images/workshop-3/frontend-app--test-list-users.png)

### Test update user

- Go back to your frontend application (at <http://localhost:5173/>).
- In the list of users, on the row of the user with `Bill Gates` name, click the `Action` button (the three dots at the end of the row).
- Click `Edit`.

  ![alt text](/images/workshop-3/frontend-app--test-update-user.png)

- Type in the new information:

  - Name: `William Henry Gates III`.
  - Email: `bill@microsoft.com`.

- Click `Save`.

  ![alt text](/images/workshop-3/frontend-app--test-create-user--confirm.png)

- You should see the updated user in the users list.

  ![alt text](/images/workshop-3/frontend-app--test-create-user--user-updated.png)

- Refresh the page and verify that the updated user is still persistent.

### Test delete user

- Go back to your frontend application (at <http://localhost:5173/>).
- In the list of users, on the row of the user with `William Henry Gates III` name, click the `Action` button (the three dots at the end of the row).
- Click `Delete`.

  ![alt text](/images/workshop-3/frontend-app--test-delete-user.png)

- Enter the email of that user `bill@microsoft.com` in the input.
- Click Delete.

  ![alt text](/images/workshop-3/frontend-app--test-delete-user--confirm.png)

- You should see the deleted user is no longer existed in the users list.

  ![alt text](/images/workshop-3/frontend-app--test-create-user--user-deleted.png)

> [!NOTE]
> Now you can be sure that the frontend works as expected, but it's still running on your local machine at <http://localhost:5173/>.

## Host the frontend application with S3 static website hosting

In this step, you will use S3 _static website hosting_ feature to

- Deploy your frontend application
- Expose it to people all over the world.

### Build your frontend application

- First, we need to build the frontend application for production by running:

  ```shell
  pnpm run build
  ```

- This will run `vite build` that produces an application bundle that is suitable to be served over a static hosting service.

- Check the application bundle at `dist`

  ```shell
  $ tree dist
  dist
  ├── assets
  │   ├── 401-BBhoy51U.js
  │   ├── 403-pH7gA2BX.js
  │   ├── 404-CUltoGn3.js
  │   ├── 500-BEjnOsrW.js
  │   ├── 503-Dw-MojSM.js
  │   └── ...
  ├── images
  │   ├── favicon_light.png
  │   ├── favicon_light.svg
  │   ├── favicon.png
  │   ├── favicon.svg
  │   └── shadcn-admin.png
  └── index.html

  3 directories, 69 files
  ```

> [!TIP]
> You can use a file server to serve the application bundle (the `dist` directory) yourself.
>
> For example, you can use [`vercel/serve`](https://github.com/vercel/serve) by running `pnpx server dist`.
>
> Now, anyone in your local network (same Wifi, LAN) can access your application.
>
> ![alt text](/images/workshop-3/frontend-app--serve-in-local-network.png)

### Hosting the application bundle with S3 static website hosting

> [!NOTE]
> Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance.
>
> - Amazon S3 is built to store and retrieve any amount of data from anywhere.
> - You can use Amazon S3 to host a static website. On a static website, individual webpages include static content. They might also contain client-side scripts.
>
> See [Hosting a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)

#### Create a S3 bucket

- Open the [S3 service](https://ap-southeast-1.console.aws.amazon.com/s3/get-started?region=ap-southeast-1&bucketType=general) in AWS Management Console
- Select `General purpose buckets` section in navigation pane.
- Click `Create bucket`

  ![alt text](/images/workshop-3/s3--list-buckets.png)

- Under `Bucket name`, enter the bucket name, e.g. `fcj-hall-of-fame`.

  > [!NOTE]
  > The bucket name must be unique within S3 global namespace.

  > [!TIP]
  > Add a suffix to your bucket name, e.g. `fcj-hall-of-fame-001`

  ![alt text](/images/workshop-3/s3--create-bucket.png)

- Keep all other settings as default.
- Scroll to the bottom and click `Create bucket`.

- You will be redirected to the list of S3 buckets.

  ![alt text](/images/workshop-3/s3--create-bucket--bucket-created.jpg)

- Click on the name of the bucket - `fcj-hall-of-fame` to see its detail.

  ![alt text](/images/workshop-3/s3--create-bucket--bucket-detail.jpg)

#### Upload frontend application bundle to S3

- Open the detail page of your S3 bucket `fcj-hall-of-fame`.

- In the `Object` tab - which is opened by default - click `Upload`.

  ![alt text](/images/workshop-3/s3--upload-objects.jpg)

- First, you need to add the files and folders you want to upload:

  - To add the `assets` folder:

    - Click `Add folder`

      ![alt text](/images/workshop-3/s3--upload-objects--add-folder.jpg)

    - Select the `assets` folder in the `dist` folder (of your frontend application)
    - Click `Upload`.

      ![alt text](/images/workshop-3/s3--upload-objects--upload-folder-assets.png)

    - Click `Upload` again to confirm upload all files from `assets`.

  - To add the `images` folder:

    - Click `Add folder`

      ![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images.png)

    - Select the `images` folder in the `dist` folder (of your frontend application)
    - Click `Upload`.

      ![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-select.png)

    - Click `Upload` again to confirm upload all files from `images`.

      ![alt text](/images/workshop-3/s3--upload-objects--upload-folder-images-confirm.png)

  - To add the `index.html` file:

    - Click `Add files`

      ![alt text](/images/workshop-3/s3--upload-objects--upload-file-index.png)

    - Select the `index.html` file in the `dist` folder (of your frontend application)
    - Click `Open`.

      ![alt text](/images/workshop-3/s3--upload-objects--upload-file-index-confirm.png)

- After add these files and folder, scroll to bottom, click `Upload`

  ![alt text](/images/workshop-3/s3--upload-objects--upload--confirm.png)

- Wait for the files and folders to be uploaded to your S3 bucket.

  ![alt text](/images/workshop-3/s3--upload-objects--upload--progress.jpg)

- When the upload is finished, you will see an `Upload succeeded` notification.

- In the `Summary` section, click on the URI of the S3 bucket (`s3://fcj-hall-of-fame`) to go back to the detail page of the bucket.

  ![alt text](/images/workshop-3/s3--upload-objects--upload--status.jpg)

#### Interact with objects in S3 bucket

- After upload the application bundle to `fcj-hall-of-fame` bucket, go back to the detail of the bucket, you will see the list of objects.

  ![alt text](/images/workshop-3/s3-bucket--list-objects.png)

- Click on the `index.html` object to see its detail.

  ![alt text](/images/workshop-3/s3-bucket--index-object.png)

- If you click on the `Object URL`, you will get an `Access Denied` response in XML.

  ![alt text](/images/workshop-3/s3-bucket--index-object--access-denied.png)

  > [!NOTE]
  > You can use the Object URL to access an object if:
  >
  > - The object allow _public access_ (it is shared with anyone in the Internet).
  > - The bucket doesn't have `Block Public access` feature turned on.

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
> When you click the Open button,
>
> - S3 generates a pre-signed URL for the object.
> - You open the object via that pre-signed URL.
>
> For more information, see [Sharing objects with pre-signed URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html)

#### Turn on S3 static website hosting

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

#### Settings permission for website access

##### Turn off S3 Block Public Access

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

##### Add a bucket policy to grant public read access to your bucket

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
