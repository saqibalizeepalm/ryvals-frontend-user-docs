# 📄 Documentation for `index.jsx`

This documentation provides a detailed explanation of the `index.jsx` file, which is designed to handle real-time notifications in a React application using WebSockets. This file is instrumental in maintaining a live connection between the client and server, enabling the delivery of notifications efficiently.

## 📚 Table of Contents

1. [Introduction](#introduction)
2. [Key Components](#key-components)
3. [Implementation Details](#implementation-details)
4. [Code Breakdown](#code-breakdown)
5. [Conclusion](#conclusion)

## 🌟 Introduction

In this file, we define a custom hook, `useNotificationSocket`, which establishes a WebSocket connection to receive real-time notifications. The hook manages the connection lifecycle, handles incoming messages, and provides a mechanism for reconnecting in case of connection loss.

## 🔑 Key Components

- **WebSocket**: A protocol for full-duplex communication channels over a single TCP connection.
- **React Redux**: Used to access the application's state and user information.
- **Custom Hook (`useNotificationSocket`)**: Encapsulates logic for WebSocket management.

## 🔍 Implementation Details

The `useNotificationSocket` hook is designed to:

- Establish a WebSocket connection when a user is logged in.
- Listen for incoming messages and process them using a callback function.
- Implement reconnection logic if the connection is lost.
- Clean up the connection on component unmount.

## 📝 Code Breakdown

Let's delve into the code and understand its functionality step-by-step.

### Import Statements

```jsx
import React, { useEffect, useRef, useState } from "react";
import { useSelector } from "react-redux";
```

- **`useEffect`**: For managing side effects in functional components.
- **`useRef`**: To hold a mutable value similar to an instance variable.
- **`useState`**: To manage component state.
- **`useSelector`**: To extract data from the Redux store state.

### Custom Hook Definition

```jsx
function useNotificationSocket({ callbackMessage = () => {} }) {
```

- **`callbackMessage`**: A function that processes incoming WebSocket messages.

### State and Ref Initialization

```jsx
const loggedUser = useSelector((state) => state);
const [reconnect, setReconnect] = useState(false);
let notificationSocketInstance = useRef(null);
```

- **`loggedUser`**: Retrieves user information from the Redux store.
- **`reconnect`**: A state variable to trigger reconnection.
- **`notificationSocketInstance`**: A mutable reference to the WebSocket instance.

### Effect for WebSocket Connection

```jsx
useEffect(() => {
    let wsCurrent;
    if (loggedUser && loggedUser.user) {
        try {
            notificationSocketInstance.current = new WebSocket(
                `${process.env.REACT_APP_SOCKET_URL}${loggedUser?.user?.id}/`
            );
            notificationSocketInstance.current.onconnect = function (msg) {
                console.log(msg, "CONNECT");
            };
            notificationSocketInstance.current.onmessage = function (msg) {
                const notificationSocketData = JSON.parse(msg.data);
                callbackMessage(notificationSocketData);
            };
            notificationSocketInstance.current.onclose = function (msg) {
                setTimeout(() => {
                    console.log("RECONNECT");
                    setReconnect(prev => !prev);
                }, 2000);
            };
            wsCurrent = notificationSocketInstance.current;
        } catch (error) {
            console.log(error);
        }
    }
    return () => {
        wsCurrent?.close();
    };
}, [loggedUser, reconnect]);
```

- **Connection Setup**: Establishes a WebSocket connection using the user's ID.
- **Event Listeners**: Handles `onconnect`, `onmessage`, and `onclose` events.
- **Reconnection Logic**: Triggers a reconnection attempt 2 seconds after connection closure.

### Effect for Monitoring Connection State

```jsx
useEffect(() => {
    console.log(notificationSocketInstance.current?.readyState, "STATE");
}, [notificationSocketInstance.current?.readyState]);
```

- **Connection State Logging**: Logs the current state of the WebSocket connection.

### Return Statement

```jsx
return notificationSocketInstance;
```

- **Return Value**: Provides access to the WebSocket instance.

## 🏁 Conclusion

The `index.jsx` file encapsulates the logic for handling WebSocket connections in a React application. It ensures reliable communication by managing connection lifecycle events and implementing reconnection strategies. This setup is crucial for applications that require real-time updates, such as notification systems.

By leveraging React hooks and Redux, this code achieves a seamless integration of WebSocket functionalities in the application's component structure.