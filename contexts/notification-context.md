# 📚 NotificationsContext.jsx Documentation

Welcome to the documentation for the `NotificationsContext.jsx` file! This file is an integral part of a React application that manages notification data, including fetching status, unread counts, and the notifications themselves. Let's dive into the details! 🚀

---

## 🎯 Overview

This file provides a **context** and **provider** to manage and distribute notification-related state across a React application. It uses React's Context API and the `useReducer` hook to maintain and update the state effectively.

## 📑 Index

1. [Import Statements](#-import-statements)
2. [Initial State](#-initial-state)
3. [Reducer Function](#-reducer-function)
4. [NotificationsProvider Component](#-notificationsprovider-component)
5. [useNotifications Hook](#-usenotifications-hook)
6. [Exported Components and Hooks](#-exported-components-and-hooks)
7. [Usage Example](#-usage-example)

---

## 🛠️ Import Statements

```jsx
import * as React from "react";
```

* All of React's functionalities are imported to use components, hooks, and context.

---

## 🏁 Initial State

```jsx
const initialState = {
  fetchNotifications: false,
  unreadCount: 0,
  notificationsData: [],
};
```

- **`fetchNotifications`**: A boolean indicating if notifications data should be fetched.
- **`unreadCount`**: An integer representing the count of unread notifications.
- **`notificationsData`**: An array to store the notifications information.

---

## 🔄 Reducer Function

### Function: `countReducer`

```jsx
function countReducer(state, action) {
  switch (action.type) {
    case "REFETCH": {
      return { ...state, fetchNotifications: action.payload };
    }
    case "UPDATE_UNREAD_COUNT": {
      return { ...state, unreadCount: action.payload };
    }
    case "UPDATE_NOTIFICATIONS_DATA": {
      console.log(action.payload,"PAYLOAD");
      return { ...state, notificationsData: action.payload };
    }
    case "SOCKET_NOTIFICATIONS_DATA": {
      const temp = state?.notificationsData?.length ? [...state?.notificationsData] : [];
      temp.unshift(action.payload);
      return { ...state, unreadCount: state.unreadCount + 1, notificationsData: temp };
    }
    default: {
      throw new Error(`Unhandled action type: ${action.type}`);
    }
  }
}
```

#### Actions:
- **`REFETCH`**: Updates whether notifications should be fetched.
- **`UPDATE_UNREAD_COUNT`**: Sets the unread notifications count.
- **`UPDATE_NOTIFICATIONS_DATA`**: Logs and updates the notifications data.
- **`SOCKET_NOTIFICATIONS_DATA`**: Handles real-time data by prepending new notifications, and increments unread count.

---

## 🧩 NotificationsProvider Component

### Function: `NotificationsProvider`

```jsx
function NotificationsProvider({ children }) {
  const [state, dispatch] = React.useReducer(countReducer, initialState);
  const value = { state, dispatch };
  return (
    <NotificationsContext.Provider value={value}>
      {children}
    </NotificationsContext.Provider>
  );
}
```

- **`NotificationsProvider`**: Encapsulates the components that need access to the notifications context.
  - **`state`**: Managed by `useReducer` with `countReducer` and `initialState`.
  - **`dispatch`**: A function to dispatch actions to the reducer.

---

## 🧰 useNotifications Hook

### Function: `useNotifications`

```jsx
function useNotifications() {
  const context = React.useContext(NotificationsContext);
  if (context === undefined) {
    throw new Error("useNotifications must be used within a CountProvider");
  }
  return context;
}
```

- **`useNotifications`**: Custom hook to access the notifications context.
  - Throws an error if used outside of the `NotificationsProvider`.

---

## ✨ Exported Components and Hooks

- **`NotificationsProvider`**: Used to wrap components that need notification state access.
- **`useNotifications`**: Custom hook to access and manipulate notifications state.

---

## 📌 Usage Example

Here's a simple example of how to use the `NotificationsContext` in a React component:

```jsx
import React from 'react';
import { NotificationsProvider, useNotifications } from './NotificationsContext';

function NotificationComponent() {
  const { state, dispatch } = useNotifications();

  React.useEffect(() => {
    if (!state.fetchNotifications) {
      dispatch({ type: 'REFETCH', payload: true });
    }
  }, [state, dispatch]);

  return (
    <div>
      <h2>Unread Notifications: {state.unreadCount}</h2>
      <ul>
        {state.notificationsData.map((notif, index) => (
          <li key={index}>{notif.message}</li>
        ))}
      </ul>
    </div>
  );
}

function App() {
  return (
    <NotificationsProvider>
      <NotificationComponent />
    </NotificationsProvider>
  );
}

export default App;
```

In this example, `NotificationComponent` utilizes the `useNotifications` hook to interact with the notifications context, displaying unread notifications and their messages.

---

Thank you for exploring the `NotificationsContext.jsx` documentation! If you have any questions or need further clarification, feel free to reach out. Happy coding! 🌟