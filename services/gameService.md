# 📜 game.service.js Documentation

Welcome to the documentation for the `game.service.js` file. This service is designed to interact with the backend API for retrieving and managing game data, including game listings, lobby details, and participant information. Below is a detailed explanation of its functionalities and purpose.

## Table of Contents

1. [Overview](#overview)
2. [Interceptors](#interceptors)
3. [Helper Function](#helper-function)
4. [Exported Functions](#exported-functions)
   - [gamelisting](#gamelisting)
   - [gameLobbyListing](#gamelobbylisting)
   - [gameLobbyDetail](#gamelobbydetail)
   - [participantList](#participantlist)

---

## Overview

This file utilizes `axios` to perform HTTP requests to the backend API. It includes functions to fetch game-related data, such as listings of available games, details of specific game lobbies, and participants within a game lobby. The service makes use of an **Authorization Token** to authenticate requests.

## Interceptors

Interceptors are used to handle responses globally, allowing for a centralized error handling mechanism.

```javascript
axiosApi.interceptors.response.use(
  (response) => response.data,
  (error) => {
    let errStatus = error.response?.status;
    // Handle HTTP status codes
    if (errStatus === 401) {
      window.location.replace("/logout");
      return;
    }
    if (errStatus === 404) {
      window.location.replace("/PageNotFound");
      return;
    }
    if (errStatus === 406) {
      window.location.replace("/vpn");
      return;
    }
    // Construct error message
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

- **401 Unauthorized:** Redirects to the logout page.
- **404 Not Found:** Redirects to a "Page Not Found" page.
- **406 Not Acceptable:** Redirects to a VPN page.

## Helper Function

### passAuthToken

A helper function that sets the `Authorization` token in the headers for authenticated requests.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

## Exported Functions

### gamelisting

Fetches a list of games from the API.

```javascript
export async function gamelisting() {
  const url = process.env.REACT_APP_APIURL + "games/";
  let headers = { "Content-Type": "application/json" };
  passAuthToken(); // Pass the Auth token
  return await axiosApi.get(url, { headers });
}
```

### gameLobbyListing

Fetches a list of game lobbies based on provided filters.

```javascript
export async function gameLobbyListing(filters) {
  const url = process.env.REACT_APP_APIURL + `games/${filters.game_slug}/lobby/`;
  let params = new URLSearchParams();
  if (filters.isPaginated) {
    if (filters.type) params.append("lobby", filters.type);
    if (filters.pageSize) params.append("page_size", filters.pageSize);
    if (filters.pageNum) params.append("page", filters.pageNum);
    if (filters?.rewardAmount) params.append("type", filters?.rewardAmount);
    if (filters?.mode) params.append("mode", filters?.mode);
  } else {
    params.append("no_page", filters.isPaginated);
    if (filters?.rewardAmount) params.append("type", filters?.rewardAmount);
  }
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers, params });
}
```

### gameLobbyDetail

Fetches the details of a specific game lobby.

```javascript
export async function gameLobbyDetail(game_slug, lobbyId) {
  const url = process.env.REACT_APP_APIURL + `games/${game_slug}/lobby/${lobbyId}/`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

### participantList

Fetches the list of participants in a specific game lobby.

```javascript
export async function participantList(game_slug, lobbyId) {
  const url = process.env.REACT_APP_APIURL + `games/${game_slug}/lobby/${lobbyId}/teammates/`;
  let headers = { "Content-Type": "application/json" };
  passAuthToken();
  return await axiosApi.get(url, { headers });
}
```

---

This concludes the documentation for the `game.service.js` file. This service is a crucial part of the application, providing essential data retrieval functionalities for gaming operations. 😄 If you have any further questions or need additional information, feel free to ask!