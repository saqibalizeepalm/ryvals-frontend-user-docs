# 📚 Notification System Documentation

This documentation provides a detailed overview of a React-based notification system composed of three key components: **NotificationCard.jsx**, **index.jsx**, and **NotificationList.jsx**. Each component plays a unique role in handling and displaying notifications to users. Below you'll find a comprehensive explanation of how each piece fits into the system.

## 🌟 Index

1. [NotificationCard.jsx](#notificationcardjsx)
2. [index.jsx](#indexjsx)
3. [NotificationList.jsx](#notificationlistjsx)

---

## 📬 NotificationCard.jsx

### Purpose

The **NotificationCard** component is responsible for rendering individual notification items. It provides interaction capabilities such as accepting or declining friend requests and navigating to related user profiles.

### Key Functionalities

- **Display Notification**: Shows the notification message and associated user profile picture.
- **Handle Friend Requests**: Provides buttons to accept or decline friend requests.
- **Navigation**: Redirects users to relevant pages based on the notification type.

### Code Breakdown

```jsx
import React from "react";
import { Button } from "react-bootstrap";
import { useHistory } from "react-router-dom";
import { toast } from "react-toastify";
import { dateStringTodayTommorrow } from "../../helper/utilities";
import { putFriendRequest } from "../../services/notifications.service";

function NotificationCard({ userData, fetchNotificationsList, setLoader, pageNum }) {
    const history = useHistory();

    const handleFriendRequest = (e, notificationAction, notificationId) => {
        e.stopPropagation();
        setLoader(true);
        putFriendRequest({ notificationAction, notificationId })
            .then((res) => {
                setLoader(false);
                fetchNotificationsList(pageNum === 1 ? true : false);
            })
            .catch((err) => {
                setLoader(false);
            });
    };

    const handleNotificationNavigate = (notification) => {
        switch (notification.type_of_notification) {
            case 1:
                history.push(`/player-profile/${notification?.from_user}`, {
                    id: notification?.from_user,
                    notificationId: notification?.id,
                    prevPath: "/notifications",
                    type: userData?.type_of_notification,
                });
                break;
            case 2:
                // Implement navigation for other notification types
                break;
            default:
                break;
        }
    };

    return (
        <div
            className="d-flex notification-box"
            style={userData?.type_of_notification !== 3 ? { cursor: "pointer" } : {}}
            onClick={() => handleNotificationNavigate(userData)}
        >
            <div className="notificationPicture">
                <img
                    src={userData?.profile_url && userData?.profile_url !== "null" ? userData?.profile_url : "/assets/images/profile-img.jpg"}
                    alt="Profile"
                    className="profilepic"
                />
            </div>
            <div className="notification-content notificationHeading">
                {userData?.message}
                <p className="notification-date">{dateStringTodayTommorrow(userData?.created)}</p>
            </div>
            {userData?.type_of_notification === 1 && (
                <>
                    <Button className="decline-btn" onClick={(e) => handleFriendRequest(e, false, userData?.id)}>
                        Decline
                    </Button>
                    <Button className="accept-btn" onClick={(e) => handleFriendRequest(e, true, userData?.id)}>
                        Accept
                    </Button>
                </>
            )}
        </div>
    );
}

export default React.memo(NotificationCard);
```

### Props

- **userData**: Notification data for rendering.
- **fetchNotificationsList**: Function to refresh the notifications list.
- **setLoader**: Function to toggle loading state.
- **pageNum**: Current page number for notifications.

---

## 📑 index.jsx

### Purpose

The **index.jsx** component acts as the main entry point for the notification system. It sets up the user interface and handles the loading state.

### Key Functionalities

- **Render Notifications Page**: Displays the main structure of the notifications page with a parallax header.
- **Loader Management**: Controls the display of a loading spinner.

### Code Breakdown

```jsx
import React, { useState } from "react";
import { Parallax } from "react-parallax";
import NotificationList from "./NotificationList";

function Notifications() {
    const [loader, setLoader] = useState(false);

    return (
        <>
            <div className="slider-activation slider-creative-agency profile-slider">
                {loader ? (
                    <div className="loading"></div>
                ) : (
                    <Parallax bgImage={"/assets/images/header-background.png"} strength={500}>
                        <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
                            <div className="container">
                                <div className="row">
                                    <div className="col-lg-12">
                                        <div className="inner text-center">
                                            <h1 className="title game-title theme-gradient">Notifications</h1>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </Parallax>
                )}
            </div>
            <NotificationList setLoader={setLoader} />
        </>
    );
}

export default Notifications;
```

### Components Used

- **Parallax**: Used for a dynamic background effect.
- **NotificationList**: Renders the list of notifications.

---

## 📄 NotificationList.jsx

### Purpose

The **NotificationList** component manages the collection of notifications, handling pagination and real-time updates.

### Key Functionalities

- **Fetch Notifications**: Loads notifications from the server with pagination support.
- **Render Notification Cards**: Displays each notification using the `NotificationCard` component.
- **Real-time Updates**: Updates notifications in real-time using context and effects.

### Code Breakdown

```jsx
import React, { useCallback, useEffect, useState } from "react";
import { useNotifications } from "../../context/NotificationsContext";
import Paginator from "../../helper/paginator/Paginator";
import { getNotificationsList, putNotificationRead } from "../../services/notifications.service";
import NotificationCard from "./NotificationCard";

function NotificationList({ setLoader }) {
    const pageSize = 25;
    const { state, dispatch: dispatchContext } = useNotifications();
    const [pageNum, setPageNum] = useState(1);
    const [notificationsData, setNotificationData] = useState(state?.notificationsData);

    const handlePageClick = (pageNum) => {
        setPageNum(pageNum);
    };

    const fetchNotificationsList = useCallback(() => {
        let filter = { isPaginated: true, pageNum, pageSize };
        setLoader(true);
        getNotificationsList(filter)
            .then((res) => {
                setNotificationData(res?.results);
                dispatchContext({ type: "UPDATE_UNREAD_COUNT", payload: res?.notifications });
                setLoader(false);
            })
            .catch((err) => {
                setLoader(false);
            });
    }, [pageNum, setLoader]);

    useEffect(() => {
        putNotificationRead().then(() => {
            dispatchContext({ type: "UPDATE_UNREAD_COUNT", payload: 0 });
        }).catch(console.log);
    }, [dispatchContext]);

    useEffect(() => {
        fetchNotificationsList();
    }, [fetchNotificationsList, pageNum]);

    useEffect(() => {
        if (state.fetchNotifications && pageNum === 1) {
            fetchNotificationsList();
        }
        dispatchContext({ type: "REFETCH", payload: false });
    }, [dispatchContext, fetchNotificationsList, pageNum, state.fetchNotifications]);

    useEffect(() => {
        if (pageNum === 1) {
            setNotificationData(state?.notificationsData);
        }
    }, [state?.notificationsData]);

    return (
        <section className="notification-outer-container">
            <div className="container">
                <div className="row">
                    <div className="col">
                        {notificationsData?.length ? (
                            <div className="notification-list">
                                <h3>NOTIFICATIONS</h3>
                            </div>
                        ) : null}
                        {notificationsData?.length ? (
                            <div className="notification-listing-box">
                                {notificationsData?.map((notificationItem) => (
                                    <NotificationCard
                                        userData={notificationItem}
                                        fetchNotificationsList={fetchNotificationsList}
                                        key={notificationItem?.id}
                                        setLoader={setLoader}
                                        pageNum={pageNum}
                                    />
                                ))}
                            </div>
                        ) : (
                            <h2 className="notifications-empty">No Notifications</h2>
                        )}
                        <div>
                            <Paginator
                                totalCount={notificationsData?.length}
                                pageSize={pageSize}
                                pageClick={handlePageClick}
                            />
                        </div>
                    </div>
                </div>
            </div>
        </section>
    );
}

export default React.memo(NotificationList);
```

### Hooks & Variables

- **useState**: Manages local state for pagination and notifications.
- **useCallback**: Optimizes performance by memoizing the fetch function.
- **useEffect**: Synchronizes notification fetching and updates.

### Context & Service Functions

- **useNotifications**: Custom hook for managing notifications context.
- **getNotificationsList**: Service function to retrieve notifications from the server.
- **putNotificationRead**: Marks notifications as read.

### Components Used

- **NotificationCard**: Renders individual notifications.
- **Paginator**: Controls pagination for the notifications list.

---

### 🚀 Conclusion

This notification system efficiently handles the display, interaction, and real-time updates of user notifications. By leveraging React's powerful hooks and context API, it provides a seamless user experience. Each component is organized to maintain readability, scalability, and ease of maintenance in the application's architecture. 

Keep exploring and building upon this baseline to enhance your application's notification features! 🌟