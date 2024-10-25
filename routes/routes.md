# 📜 Routes.js Documentation

Welcome to the documentation for the `Routes.js` file. This file plays a crucial role in defining the routing structure of our application by specifying different routes and their corresponding components. Understanding the routes is essential for navigating through the application and implementing new features effectively. Let's explore the details! 🚀

---

## 📋 Index

1. [Introduction](#introduction)
2. [Imports](#imports)
3. [Routes Overview](#routes-overview)
   - [Public Routes](#public-routes)
   - [Auth Routes](#auth-routes)
   - [Private Routes](#private-routes)
4. [Exported Routes](#exported-routes)
5. [Conclusion](#conclusion)

---

## 📌 Introduction

The `Routes.js` file is responsible for defining and exporting three major categories of routes:
- **Public Routes**: Accessible to all users, regardless of their authentication status.
- **Auth Routes**: Specifically for authentication-related paths like login and registration.
- **Private Routes**: Accessible only to authenticated users.

These routes are vital as they dictate the navigation flow and access control within the application.

---

## 📥 Imports

This section lists all the imported components used in the routing configuration.

```javascript
import React from "react";
import { Redirect } from "react-router-dom";
import Home from "../component/home/Home";
import Login from "../component/auth/login";
import Register from "../component/auth/register";
import ForgotPassword from "../component/auth/forget-password";
import GamesList from "../component/games/GamesList";
import LobbyList from "../component/Lobby/LobbyList";
import LobbyDetail from "../component/Lobby/LobbyDetail";
import Faq from "../component/faq/Faq";
import PPK from "../component/faq/PPK";
import MyProfile from "../component/myprofile/MyProfile";
import ResetPassword from "../component/auth/reset-password";
import accountVerification from "../component/auth/account-verification";
import Dashboard from "../component/dashboard/Dashboard";
import PrivacyPolicy from "../component/privacy/PrivacyPolicy";
import CaliforniaPrivacy from "../component/privacy/CaliforniaPrivacy";
import TermsOfUse from "../component/privacy/TermsOfUse";
import Logout from "../component/auth/Logout";
import VpnWarning from "../component/vpn/VpnWarning";
import BrandGuidelines from "../component/brandguidelines/BrandGuidelines";
import PageNotFound from "../component/vpn/PageNotFound";
import StripeForm from "../component/payment/StripeForm";
import SignUpSuccess from "../component/auth/signup-successful";
import ManageCookies from "../home/ManageCookies";
import Community from "../component/communityPage/Community";
import Notifications from "../component/notifications";
import PlayerProfile from "../component/myprofile/PlayerProfile";
```

### Explanation

Each import statement brings in a specific React component that corresponds to a particular route in the application. These components are laid out in different sections of the app, such as home, authentication, games, etc.

---

## 🛣️ Routes Overview

### Public Routes

Public routes are accessible to any user, whether authenticated or not. These typically include general information pages and open resources.

```javascript
const publicRoutes = [
  { path: "/", component: Home },
  { path: "/home", component: Home },
  { path: "/games", component: GamesList },
  { path: "/faq", component: Faq },
  { path: "/ppk", component: PPK },
  { path: "/privacy-policy", component: PrivacyPolicy },
  { path: "/california-privacy", component: CaliforniaPrivacy },
  { path: "/terms-of-use", component: TermsOfUse },
  { path: "/vpn", component: VpnWarning },
  { path: "/PageNotFound", component: PageNotFound },
  { path: "/:slug/lobby", component: LobbyList },
  { path: "/:slug/lobby/:lobbyId", component: LobbyDetail },
  { path: "/BrandGuidelines", component: BrandGuidelines },
  { path: "/manage-cookies", component: ManageCookies },
  { path: "/community", component: Community },
  // This route should be at the end of all other routes
  // { path: "*", exact: true, component: () => <Redirect to="/" /> },
];
```

### Auth Routes

Auth routes handle user authentication processes like login, signup, and account verification.

```javascript
const authRoutes = [
  { path: "/signin", component: Login },
  { path: "/signup", component: Register },
  { path: "/verifyEmail", component: SignUpSuccess },
  { path: "/forgot-password", component: ForgotPassword },
  { path: "/reset-password", component: ResetPassword },
  { path: "/verification", component: accountVerification },
];
```

### Private Routes

Private routes are protected and can be accessed only by logged-in users. These include user-specific functionalities like profile management and dashboard access.

```javascript
const privateRoutes = [
  { path: "/myprofile", component: MyProfile },
  { path: "/player-profile/:playerId", component: PlayerProfile },
  { path: "/dashboard", component: Dashboard },
  { path: "/logout", component: Logout },
  { path: "/payment", component: StripeForm },
  { path: "/notifications", component: Notifications },
];
```

---

## 📤 Exported Routes

Finally, the routes are exported for use in other parts of the application:

```javascript
export { publicRoutes, authRoutes, privateRoutes };
```

These exports allow the routes to be integrated into the application's main routing system, where they can be utilized to render the appropriate components based on the user's navigation and authentication status.

---

## 🚀 Conclusion

The `Routes.js` file is a central piece in structuring the navigation and access control of the application. By organizing routes into public, auth, and private categories, it ensures that users have a seamless experience while maintaining secure access to sensitive areas of the application. This modular approach makes it straightforward to manage and expand routing as the application grows.

Feel free to explore these routes and add new ones as needed! 🌟