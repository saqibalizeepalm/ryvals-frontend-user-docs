# Community Service Documentation 📜

This documentation provides an overview of the `community.service.js` file, which is part of a JavaScript/Node.js application. This service is responsible for interacting with a backend API to manage community-related data and functionalities.

## Index
- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Axios Interceptor Configuration](#axios-interceptor-configuration)
- [Helper Function](#helper-function)
- [Functions](#functions)
  - [communitylisting](#communitylisting)
  - [getTopPlayerList](#getTopPlayerList)

## Introduction
The `community.service.js` file is a service module designed to handle API requests related to community features. It utilizes Axios for HTTP requests and manages authentication tokens for secure API communication.

## Dependencies
- **Axios**: A promise-based HTTP client for the browser and Node.js.
- **AuthToken**: A helper module that provides the authentication token required for API access.

## Axios Interceptor Configuration
The Axios instance (`axiosApi`) is configured with an interceptor to handle responses and errors globally.

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
        if (errRes[key] instanceof Array) errMsg += errRes[key][0] + " ";
        else errMsg += errRes[key] + " ";
      }
    }
    return Promise.reject(errMsg);
  }
);
```

### Error Handling
- **401 Unauthorized**: Redirects to the logout page.
- **406 Not Acceptable**: Redirects to the VPN page.
- **Other Errors**: Constructs an error message from the response and rejects the promise.

## Helper Function
### passAuthToken
Adds the authorization token to the headers of the Axios instance.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

## Functions

### communitylisting
Fetches a list of communities from the server.

- **URL**: `/players/community/`
- **Method**: `GET`

```javascript
export async function communitylisting() {
  const url = process.env.REACT_APP_APIURL + `players/community/`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

### getTopPlayerList
Retrieves the top player list from the server.

- **URL**: `/players/top-players/`
- **Method**: `GET`

```javascript
export async function getTopPlayerList() {
  const url = process.env.REACT_APP_APIURL + `players/top-players/`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

## Conclusion
The `community.service.js` file is essential for managing community-related data through API requests. It ensures secure communication by handling authentication tokens and provides error handling through Axios interceptors, making it robust for handling API responses.