# AuthService.js Documentation 📚✨

Welcome to the documentation for **authService.js**! This file is an integral part of a web application, responsible for handling all authentication-related tasks using RESTful APIs. It utilizes Axios for HTTP requests and includes user login, signup, password recovery, and social media authentication features. Let's dive in!

## Table of Contents
1. [Overview](#overview)
2. [Setup](#setup)
3. [Functions](#functions)
    - [login](#login)
    - [signup](#signup)
    - [forgotpassword](#forgotpassword)
    - [forgotusername](#forgotusername)
    - [resetpassword](#resetpassword)
    - [verifyaccount](#verifyaccount)
    - [requestverification](#requestverification)
    - [logout](#logout)
    - [validateTwitch](#validatetwitch)
    - [twitchUserData](#twitchuserdata)
    - [discordLogin](#discordlogin)
    - [twitchLogin](#twitchlogin)
    - [facebookLogin](#facebooklogin)
    - [googleLogin](#googlelogin)
    - [twitterUrl](#twitterurl)
    - [twitterLogin](#twitterlogin)
4. [Interceptors](#interceptors)
5. [Environment Variables](#environment-variables)
6. [Conclusion](#conclusion)

---

## Overview

The **authService.js** file is a JavaScript module that implements various user authentication functionalities using Axios HTTP client. It provides mechanisms for both traditional and social media logins, error handling, and user session management. 🚀

## Setup

Before using this service, ensure that the necessary environment variables are set up correctly as they are essential for building URLs and client configurations.

## Functions

### login
**Purpose**: Authenticates a user using their email, password, and IP address.

```javascript
login({ email, password, player_ip })
```

- **Parameters**: An object containing `email`, `password`, and `player_ip`.
- **Returns**: User data on successful authentication.

### signup
**Purpose**: Registers a new user account.

```javascript
signup(model)
```

- **Parameters**: An object `model` containing user registration details.
- **Returns**: Response from the signup endpoint.

### forgotpassword
**Purpose**: Initiates the password recovery process for a user.

```javascript
forgotpassword(email)
```

- **Parameters**: User's `email` for password recovery.
- **Returns**: Response from the forgot-password endpoint.

### forgotusername
**Purpose**: Recovers a user's username via their email.

```javascript
forgotusername(email)
```

- **Parameters**: User's `email` for username recovery.
- **Returns**: Response from the forgot-username endpoint.

### resetpassword
**Purpose**: Resets a user’s password using a token and ID.

```javascript
resetpassword(password, id, token)
```

- **Parameters**: `password`, `id`, and `token`.
- **Returns**: Response from the reset-password endpoint.

### verifyaccount
**Purpose**: Verifies a user account using token and ID.

```javascript
verifyaccount(id, token)
```

- **Parameters**: `id` and `token`.
- **Returns**: Response from the verification endpoint.

### requestverification
**Purpose**: Requests a new account verification email.

```javascript
requestverification(email)
```

- **Parameters**: User's `email`.
- **Returns**: Response from the resend-verification-email endpoint.

### logout
**Purpose**: Logs out the user and clears their session data.

```javascript
logout()
```

- **Returns**: None

### validateTwitch
**Purpose**: Validates a Twitch token.

```javascript
validateTwitch(data)
```

- **Parameters**: Twitch token (`data`).
- **Returns**: Response from Twitch validation endpoint.

### twitchUserData
**Purpose**: Fetches Twitch user data.

```javascript
twitchUserData(user, token)
```

- **Parameters**: `user` ID and `token`.
- **Returns**: Twitch user data.

### discordLogin
**Purpose**: Logs in a user using Discord authentication.

```javascript
discordLogin(data)
```

- **Parameters**: Discord login `data`.
- **Returns**: Response from social-login endpoint.

### twitchLogin
**Purpose**: Logs in a user using Twitch authentication.

```javascript
twitchLogin(data)
```

- **Parameters**: Twitch login `data`.
- **Returns**: Response from social-login endpoint.

### facebookLogin
**Purpose**: Logs in a user using Facebook authentication.

```javascript
facebookLogin(data)
```

- **Parameters**: Facebook login `data`.
- **Returns**: Response from social-login endpoint.

### googleLogin
**Purpose**: Logs in a user using Google authentication.

```javascript
googleLogin(data)
```

- **Parameters**: Google login `data`.
- **Returns**: Response from social-login endpoint.

### twitterUrl
**Purpose**: Fetches authentication URL for Twitter.

```javascript
twitterUrl({ redirect })
```

- **Parameters**: `redirect` URL.
- **Returns**: Twitter authentication URL.

### twitterLogin
**Purpose**: Logs in a user using Twitter authentication.

```javascript
twitterLogin(data)
```

- **Parameters**: Twitter login `data`.
- **Returns**: Response from social-login endpoint.

## Interceptors

Axios interceptors are used in this file to handle the responses globally:

- **401 Error**: Redirects to logout if unauthorized.
- **406 Error**: Redirects to VPN page after 3 seconds.
- **500 Error**: Displays a toast notification with an error message.

## Environment Variables

The following environment variables are expected by this file:
- `REACT_APP_APIURL`
- `REACT_APP_DISCORD_CLIENT_ID`
- `REACT_APP_DISCORD_CLIENT_SECRET_KEY`
- `REACT_APP_TWITCH_CLIENT_ID`

Ensure these are configured correctly for the authentication services to work.

## Conclusion

The **authService.js** module provides a comprehensive solution for handling user authentication in a web application. From traditional email/password logins to social media authentication via Discord, Twitch, Facebook, Google, and Twitter, this service ensures a smooth and secure user experience. 🛡️💻

Feel free to explore the code and integrate it with your application for robust authentication capabilities!