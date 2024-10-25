# Documentation for `lobbies.service.js` 📚

This documentation provides an overview and explanation of the `lobbies.service.js` file, which is responsible for managing API interactions related to game lobbies within a web application. This service is built using Axios for HTTP requests and includes mechanisms for handling authentication and error responses.

---

## Table of Contents
1. [Overview](#overview)
2. [Interceptor Setup](#interceptor-setup)
3. [Functions](#functions)
   - [getAvailableLobbies](#getavailablelobbies)
   - [getActiveLobbies](#getactivelobbies)
   - [getPreviousLobbies](#getpreviouslobbies)
   - [callGameFilter](#callgamefilter)
4. [Utility Functions](#utility-functions)
   - [passAuthToken](#passauthtoken)

---

## Overview

The `lobbies.service.js` file is a service layer used to handle HTTP requests related to different categories of game lobbies. These requests are authenticated using a token and handle various HTTP response statuses to ensure a smooth user experience.

**Key Libraries Used:**
- **Axios**: Used for making HTTP requests.
- **AuthToken**: A helper function to attach authorization tokens to requests.

---

## Interceptor Setup

The Axios instance (`axiosApi`) is configured with an interceptor to process responses and handle errors.

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
    // Process other errors
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

**Error Handling:**
- **401 Unauthorized**: Redirects to the logout page.
- **406 Not Acceptable**: Redirects to a VPN-related page.
- **Other Errors**: Compiles error messages and rejects the promise with a concatenated error message.

---

## Functions

### getAvailableLobbies

Fetches the list of available lobbies from the server.

```javascript
export async function getAvailableLobbies() {
  const url = process.env.REACT_APP_APIURL + "players/dashboard/available-lobbies/";
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Endpoint**: `/players/dashboard/available-lobbies/`
- **Description**: Retrieves available lobbies for players.
- **Authentication**: Requires an authorization token.

### getActiveLobbies

Fetches the list of active lobbies.

```javascript
export async function getActiveLobbies() {
  const url = process.env.REACT_APP_APIURL + "players/dashboard/active-lobbies/";
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Endpoint**: `/players/dashboard/active-lobbies/`
- **Description**: Retrieves currently active lobbies.
- **Authentication**: Requires an authorization token.

### getPreviousLobbies

Fetches the list of previous lobbies.

```javascript
export async function getPreviousLobbies() {
  const url = process.env.REACT_APP_APIURL + "players/dashboard/previous-lobbies/";
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Endpoint**: `/players/dashboard/previous-lobbies/`
- **Description**: Retrieves lobbies that players have previously engaged with.
- **Authentication**: Requires an authorization token.

### callGameFilter

Filters available lobbies by a specific game.

```javascript
export async function callGameFilter(filter) {
  const url = process.env.REACT_APP_APIURL + `players/dashboard/available-lobbies/?game=${filter}`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Endpoint**: `/players/dashboard/available-lobbies/?game=<filter>`
- **Description**: Filters available lobbies based on the game specified by the `filter` parameter.
- **Authentication**: Requires an authorization token.

---

## Utility Functions

### passAuthToken

Attaches the authorization token to the Axios instance headers.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

- **Purpose**: Ensures that all requests made using the `axiosApi` instance are authenticated with a valid token.

---

This file plays a crucial role in managing the user's interaction with game lobbies, ensuring secure, efficient, and user-friendly access to the game's lobby data. 🕹️🎮