# User Service Documentation 📄

The `user.service.js` file contains a set of functions that interact with the API endpoints related to user management. It handles everything from getting and updating user details, managing gaming accounts, handling user authentication, managing friends, wallet operations, social media linkage, and more.

## Table of Contents 📑

- [Overview](#overview)
- [Setup](#setup)
- [API Functions](#api-functions)
  - [User Profile Management](#user-profile-management)
  - [Gaming Account Management](#gaming-account-management)
  - [Lobby Enrollment](#lobby-enrollment)
  - [Complaint Handling](#complaint-handling)
  - [Wallet Operations](#wallet-operations)
  - [Country and Region Data](#country-and-region-data)
  - [OTP and Password Management](#otp-and-password-management)
  - [Social Media Integration](#social-media-integration)
  - [Friend Management](#friend-management)
  - [Search and Protection](#search-and-protection)
  - [Avatar and Azure Token](#avatar-and-azure-token)
- [Error Handling](#error-handling)
- [Conclusion](#conclusion)

## Overview

The `user.service.js` facilitates communication between the client and the server, primarily for user-related actions. Utilizing Axios, the service handles HTTP requests, processes responses, and manages errors efficiently. 

## Setup

```javascript
import axios from "axios";
import AuthToken from "../helper/authToken";
import toastify from "../helper/toastify";

const axiosApi = axios.create();
```

### Interceptors

The Axios instance is equipped with interceptors to manage responses and errors effectively, ensuring smooth user experiences.

## API Functions

### User Profile Management

- **getUserDetail**: Fetches the details of the logged-in user and stores it in local storage.
- **editUserDetail**: Allows editing of the user's profile information.

### Gaming Account Management

- **addGamerTag**: Adds a new gamer tag to the user's profile.
- **editGamerTag**: Updates an existing gamer tag for a specified game.

### Lobby Enrollment

- **enrollForGame**: Enrolls the user in a game lobby using lobby ID, player IP, and promotional choice.

### Complaint Handling

- **fileComplaint**: Sends a complaint to the server with the provided model data.

### Wallet Operations

- **getWalletBalance**: Retrieves the user's wallet balance.
- **addAmountToWallet**: Adds funds to the user's wallet using Stripe.
- **redeemAmount**: Redeems funds from the user's wallet.
- **walletHistory**: Retrieves the transaction history for the user's wallet.

### Country and Region Data

- **getCountries**: Fetches a list of available countries.
- **getStates**: Retrieves states for a given country ID.

### OTP and Password Management

- **resendOTPapi**: Resends the OTP to the user.
- **verifyOTP**: Verifies the OTP provided by the user.
- **changeUserPassword**: Allows the user to change their password.

### Social Media Integration

- **facebookLogin**: Links the user's Facebook account.
- **googleLogin**: Links the user's Google account.
- **twitchLogin**: Links the user's Twitch account.
- **discordLogin**: Links the user's Discord account.
- **twitterLogin**: Links the user's Twitter account.
- **disconnectSocials**: Disconnects linked social media accounts.

### Friend Management

- **getFriendLists**: Retrieves the user's friend list.
- **sendFriendRequest**: Sends a friend request to another user.
- **sendAddTofavourites**: Adds a user to the favorites list.
- **removeFriendFromList**: Removes a user from the friend list.
- **replaceFavFriend**: Replaces a favorite friend with another user.

### Search and Protection

- **getSearchData**: Searches for users based on the provided filter model.
- **protectAccountData**: Protects the user's account data by setting it to private.

### Avatar and Azure Token

- **uploadAvatarImage**: Uploads an avatar image for the user profile.
- **getAzureToken**: Retrieves an Azure SAS token for further use.

## Error Handling

The service uses Axios interceptors to manage errors globally. Errors like unauthorized access (401), server errors (500), and others trigger specific actions like redirects or display toast notifications.

## Conclusion

The `user.service.js` file provides comprehensive functions to manage user data and interactions with a server API. By centralizing these operations, it ensures a consistent and efficient approach to managing user-related actions in the application. 🚀

This documentation should assist developers with understanding the purpose and usage of each function within the `user.service.js` file, contributing to more efficient code maintenance and feature implementation.