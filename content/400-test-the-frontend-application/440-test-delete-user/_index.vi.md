---
title: "Test delete user"
weight: 4
chapter: false
pre: " <b> 4.4 </b> "
---

1. Go back to your frontend application (at <http://localhost:5173/>).
2. In the list of users, on the row of the user with `William Henry Gates III` name, click the `Action` button (the three dots at the end of the row).
3. Click `Delete`.

![alt text](/images/workshop-3/frontend-app--test-delete-user.png)

4. Enter the email of that user `bill@microsoft.com` in the input.
5. Click Delete.

![alt text](/images/workshop-3/frontend-app--test-delete-user--confirm.png)

6. You should see the deleted user is no longer existed in the users list.

![alt text](/images/workshop-3/frontend-app--test-create-user--user-deleted.png)

> [!NOTE]
> Now you can be sure that the frontend works as expected, but it's still running on your local machine at <http://localhost:5173/>.
