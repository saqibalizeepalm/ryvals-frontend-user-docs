# 📄 Documentation for `teams.service.js`

This file is a **service module** that handles API requests related to team functionalities within a gaming platform. It leverages the `axios` library for making HTTP requests and includes several helper functions to manage team-related operations.

## 📚 Table of Contents
- [Overview](#overview)
- [Dependencies](#dependencies)
- [Interceptors](#interceptors)
- [Functions](#functions)
  - [getTeamMatesLobby](#getteammateslobby)
  - [postFriendRequest](#postfriendrequest)
  - [postReplaceTeamMate](#postreplaceteammate)
  - [callPreMadeTeams](#callpremadeteams)
- [Helper Methods](#helper-methods)

## 🔍 Overview
The `teams.service.js` file provides various functions to interact with a backend API for managing teams in a gaming context. It includes functionalities like fetching teammates in a lobby, sending friend requests, replacing team members, and retrieving pre-made teams.

## 📦 Dependencies
The file imports several modules:
- **axios**: For making HTTP requests.
- **AuthToken**: A helper function to attach authentication tokens to request headers.
- **toastify**: A notification library used for displaying error messages.

```javascript
import axios from "axios";
import AuthToken from "../helper/authToken";
import toastify from "../helper/toastify";
```

## 🔗 Interceptors
An interceptor is configured to handle responses, particularly errors. It processes error responses and performs redirection or error message handling based on the HTTP status code.

```javascript
axiosApi.interceptors.response.use(
  (response) => response.data,
  (error) => {
    let errStatus = error.response.status;
    if (errStatus === 401) {
      window.location.replace("/logout"); // Redirect to logout
      return;
    }
    if (errStatus === 406) {
      setTimeout(() => {
        window.location.replace("/vpn");
      }, 3000); // Redirect after a delay
      return;
    }
    if (errStatus === 500) {
      toastify(
        "error",
        error.response.data.error === "Please verify your account" ? error.response.data.error : error.response.data.detail
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

## 🛠️ Functions

### getTeamMatesLobby
Fetches the list of teammates in a specific lobby.

```javascript
export async function getTeamMatesLobby({ lobby_id, teamId }) {
  const url = process.env.REACT_APP_APIURL + `players/lobby/${lobby_id}/teammates/${teamId ? "?team=" + teamId : ""}`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Parameters**: Accepts an object with properties `lobby_id` and optionally `teamId`.
- **Returns**: A promise resolving to a list of teammates.

### postFriendRequest
Handles sending or responding to friend requests within the lobby.

```javascript
export async function postFriendRequest({ status, promo_choice, lobbyId, teamId }) {
  const url = process.env.REACT_APP_APIURL + `players/lobby/${lobbyId}/${teamId}/${status}-invite/`;
  let headers = { "Content-Type": "application/json" };
  let body = { promo_choice: promo_choice };
  passAuthToken();
  return await axiosApi.post(url, body, { headers });
}
```

- **Parameters**: An object containing `status`, `promo_choice`, `lobbyId`, and `teamId`.
- **Returns**: A promise indicating the success or failure of the request.

### postReplaceTeamMate
Replaces a teammate in a specific lobby.

```javascript
export async function postReplaceTeamMate({ lobbyId, teamId, removeId, newId }) {
  const url = process.env.REACT_APP_APIURL + `players/lobby/${lobbyId}/${teamId}/replace-teammate/`;
  let headers = { "Content-Type": "application/json" };
  let body = { "remove_player": removeId, "new_player": newId };
  passAuthToken();
  return await axiosApi.post(url, body, { headers });
}
```

- **Parameters**: An object with `lobbyId`, `teamId`, `removeId`, and `newId`.
- **Returns**: A promise indicating the success or failure of the operation.

### callPreMadeTeams
Retrieves pre-made teams available in a lobby.

```javascript
export async function callPreMadeTeams(lobby_id) {
  const url = process.env.REACT_APP_APIURL + `players/lobby/${lobby_id}/existing-teams/`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

- **Parameters**: `lobby_id` - The ID of the lobby.
- **Returns**: A promise resolving to a list of existing teams.

## 🛡️ Helper Methods

### passAuthToken
Adds an authorization token to the request headers.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

- **Purpose**: Ensures that each request is authenticated by attaching a token.

---

This file plays an essential role in managing team-related activities in the gaming environment, facilitating the interaction with the server and ensuring that all actions are properly authenticated.