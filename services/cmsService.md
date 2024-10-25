# Documentation for `cms.service.js` 📄

Welcome to the documentation for the **CMS Service** module! This file provides a utility to interact with a **Content Management System (CMS)** through API requests. The main purpose is to fetch static page content programmatically, using the Axios library for HTTP requests.

## Table of Contents 🔍
1. [Introduction](#introduction)
2. [Dependencies](#dependencies)
3. [Axios Configuration](#axios-configuration)
4. [Helper Function](#helper-function)
5. [Exported Function](#exported-function)
6. [Error Handling](#error-handling)
7. [Conclusion](#conclusion)

## Introduction ✨
The `cms.service.js` file is designed to communicate with a CMS system. It primarily fetches static page data by sending HTTP GET requests to a specified API endpoint. This file uses Axios, a promise-based HTTP client, to manage these requests efficiently.

## Dependencies 📦
The module relies on the following dependencies:
- **axios**: A promise-based HTTP client for the browser and Node.js.
- **authToken**: A helper function from `../helper/authToken` that provides an authorization token.

```javascript
import axios from "axios";
import AuthToken from "../helper/authToken";
```

## Axios Configuration ⚙️
An instance of Axios is created using `axios.create()`. The instance is configured with an interceptor that processes responses:
- **Responses** return the data directly.
- **Errors** are handled based on HTTP status codes.

```javascript
const axiosApi = axios.create();
```

### Error Handling Interceptor 🔄
The interceptor checks the HTTP status of a response:
- **401 Unauthorized**: Redirects to the logout page.
- **406 Not Acceptable**: Redirects to a VPN page.
- For other errors, it compiles an error message by iterating over the error response data.

```javascript
axiosApi.interceptors.response.use(
  (response) => response.data,
  (error) => {
    let errStatus = error.response?.status;
    if (errStatus === 401) {
      window.location.replace("/logout");
      return;
    }
    if (errStatus === 406) {
      window.location.replace("/vpn");
      return;
    }
    let errRes = error.response?.data;
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

## Helper Function 🛠️

### `passAuthToken`
This function sets a default `Authorization` header for all requests using the authorization token obtained from `AuthToken`.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

## Exported Function 📤

### `getCMSData(body)`
This asynchronous function fetches CMS data for a given page title. It constructs a URL using the title provided in the `body` parameter and sends a GET request with the necessary headers.

- **Parameters**:
  - `body`: An object containing the `title` of the page to fetch.

- **Returns**: A promise resolved with the CMS data or rejected with an error message.

```javascript
export async function getCMSData(body) {
  const url = process.env.REACT_APP_APIURL + `pages/static/${body.title}`;
  let headers = {
    "Content-Type": "application/json",
  };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

## Conclusion 🎯
The `cms.service.js` file is a crucial utility for retrieving static content from a CMS. It uses Axios for HTTP requests and includes error handling and authorization token management. By encapsulating these functionalities, the service provides a streamlined and consistent interface for CMS data retrieval.

Feel free to integrate and extend this service according to your project's needs! 🚀