# Documentation for `notifications.service.js` 📬

The `notifications.service.js` file is a JavaScript module designed to handle notification-related API requests within an application. It utilizes the Axios library to perform HTTP requests, managing user authentication through tokens, and provides functions to interact with the notifications endpoint of a server API.

## Table of Contents
- [Setup and Configuration](#setup-and-configuration)
- [Functions Overview](#functions-overview)
  - [getNotificationsList](#getnotificationslist)
  - [putFriendRequest](#putfriendrequest)
  - [putNotificationRead](#putnotificationread)
- [Error Handling](#error-handling)
- [Utilities](#utilities)

## Setup and Configuration 🔧

The module imports necessary dependencies and initializes an Axios instance:

```javascript
import axios from "axios";
import AuthToken from "../helper/authToken";
import toastify from "../helper/toastify";

const axiosApi = axios.create();
```

- **AuthToken**: A helper module used to retrieve authentication tokens.
- **toastify**: A helper module for displaying notification messages to the user.

## Functions Overview 🛠️

### getNotificationsList

Fetches a list of notifications from the server, with optional pagination and sorting parameters.

```javascript
export async function getNotificationsList({ isPaginated, pageNum, pageSize, column, order })
```

- **Parameters**:
  - `isPaginated`: Boolean indicating if pagination should be used.
  - `pageNum`: (Optional) Page number for pagination.
  - `pageSize`: (Optional) Number of items per page.
  - `column`: (Optional) Column by which to sort the notifications.
  - `order`: (Optional) Order of sorting (e.g., ascending or descending).

- **Returns**: A promise resolving with the data from the server, or a rejected promise with an error message.

### putFriendRequest

Updates the status of a friend request notification.

```javascript
export async function putFriendRequest({ notificationId, notificationAction })
```

- **Parameters**:
  - `notificationId`: ID of the notification to update.
  - `notificationAction`: The action/status to set (e.g., "accept" or "reject").

- **Returns**: A promise resolving with the server response data.

### putNotificationRead

Marks all notifications as read.

```javascript
export async function putNotificationRead()
```

- **Returns**: A promise resolving with the server response data.

## Error Handling 🚨

Error handling is managed through Axios interceptors:

```javascript
axiosApi.interceptors.response.use(
  (response) => response.data,
  (error) => {
    let errStatus = error.response.status;
    if (errStatus === 401) {
      window.location.replace("/logout");
      return;
    }
    if (errStatus === 406) {
      setTimeout(() => {
        window.location.replace("/vpn");
      }, 3000);
      return;
    }
    if (errStatus === 500) {
      toastify(
        "error",
        error.response.data.error === "Please verify your account"
          ? error.response.data.error
          : error.response.data.detail
      );
    }
    let errRes = error.response.data;
    let errMsg = "";
    for (const key in errRes) {
      if (Object.hasOwnProperty.call(errRes, key)) {
        if (errRes[key] instanceof Array) errMsg = errMsg + errRes[key][0] + " ";
        else errMsg = errMsg + errRes[key] + " ";
      }
    }
    return Promise.reject(errMsg);
  }
);
```

- **401 Unauthorized**: Redirects the user to the logout page.
- **406 Not Acceptable**: Redirects to a VPN page after a delay.
- **500 Internal Server Error**: Displays an error message using `toastify`.

## Utilities 🔌

### passAuthToken

A utility function to set the Authorization header for Axios requests.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

- **Purpose**: Ensures that each request includes a valid authentication token, maintaining secure communication with the API.

By leveraging these functions and utilities, `notifications.service.js` effectively manages notifications within the application, ensuring smooth user interactions and robust error handling.