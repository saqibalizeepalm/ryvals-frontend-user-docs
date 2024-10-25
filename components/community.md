# 📜 Community.jsx Documentation

**Table of Contents**

1. [Introduction](#introduction)
2. [Imports](#imports)
3. [Component Overview](#component-overview)
4. [State Variables](#state-variables)
5. [Functions](#functions)
6. [Return Statement](#return-statement)
7. [Key Components](#key-components)
8. [Styling and Layout](#styling-and-layout)
9. [Conclusion](#conclusion)

---

## Introduction

The **Community.jsx** file is a React component designed to display a community page for a gaming or social platform. This component showcases top players, their achievements, and user-submitted content. It promotes community engagement through clip submissions and social media interactions.

---

## Imports

The file imports several modules and components to aid in functionality and styling:

| Module/Component                        | Description                                        |
|-----------------------------------------|----------------------------------------------------|
| `React`, `useState`, `useEffect`        | Core React functionalities for component state and lifecycle management. |
| `Parallax`                              | A parallax effect for backgrounds from `react-parallax`. |
| `ReactPlayer`                           | A player for embedding videos.                     |
| `Link`                                  | Routing function from `react-router-dom`.          |
| `communitylisting`, `getTopPlayerList`  | Service functions for fetching community data.     |
| `Button`, `Modal`, `Form`, `Placeholder`, `Col`, `Row` | UI components from `react-bootstrap` for layout and interaction. |

---

## Component Overview

The `Community` component is a functional component that utilizes React hooks to manage state and lifecycle events. It also integrates third-party libraries for video playback, styling, and parallax effects.

---

## State Variables

The component employs several state variables:

| State Variable   | Type    | Initial Value | Purpose                                        |
|------------------|---------|---------------|------------------------------------------------|
| `show`           | Boolean | `false`       | Controls the visibility of the clip submission modal. |
| `community`      | Array   | `[]`          | Stores community data fetched from a service.  |
| `players`        | Array   | `[]`          | Stores the top player data.                    |
| `spinnerLoader`  | Boolean | `false`       | Manages the loading spinner visibility during data fetching. |
| `playing`        | Boolean | `false`       | Controls video playback state.                 |

---

## Functions

### handleClose

```jsx
const handleClose = () => setShow(false);
```

- **Purpose**: Closes the modal by setting `show` to `false`.

### handleShow

```jsx
const handleShow = () => setShow(true);
```

- **Purpose**: Opens the modal by setting `show` to `true`.

### useEffect for Initialization

```jsx
useEffect(() => {
    getCommunityList();
    getPlayerList();
    window.addEventListener("storage", function (event) {
        if (event.key === "logout-event") {
            window.location.reload();
        }
    }, false);
}, []);
```

- **Purpose**: Fetches community and player data upon component mount and reloads the page when a logout event is detected.

### getCommunityList

```jsx
const getCommunityList = () => {
    setSpinnerLoader(true);
    communitylisting()
        .then((res) => {
            setCommunity(res);
            setSpinnerLoader(false);
        })
        .catch(() => {
            setSpinnerLoader(false);
        });
};
```

- **Purpose**: Fetches community data and updates the `community` state. Handles loading state with `spinnerLoader`.

### getPlayerList

```jsx
const getPlayerList = () => {
    getTopPlayerList().then((res) => {
        setTopPlayers(res);
    });
};
```

- **Purpose**: Fetches and sets top player data.

### startPlaying

```jsx
const startPlaying = () => {
    setPlaying(true);
};
```

- **Purpose**: Initiates video playback by setting `playing` to `true`.

---

## Return Statement

The `return` statement encompasses the JSX structure of the component. It is divided into sections that render different parts of the community page:

- **Parallax Header**: Displays a parallax background with a title.
- **Player of the Week**: Lists top players and their statistics.
- **Kill Streaks of the Week**: Shows community-submitted video clips.
- **Community Socials**: Provides links to social media platforms.
- **Modal**: A form for submitting clips.

---

## Key Components

### Parallax Header

- Utilizes the `Parallax` component to create a dynamic background effect.

### Player of the Week

- Displays the top three players with their usernames, total winnings, and total kills.

### Kill Streaks Section

- Uses `ReactPlayer` to embed video clips submitted by the community.
- Includes a submission button that opens a modal.

### Modal for Clip Submission

- Provides instructions for submitting a clip via email.

### Social Media Links

- Encourages users to follow and tag the platform's social media accounts.

---

## Styling and Layout

- **Bootstrap Grid System**: Utilizes Bootstrap's grid system (`Row`, `Col`) for responsive design.
- **CSS Classes**: Custom styling is applied through CSS classes such as `slider-activation`, `player-of-the-week`, and `community-socials`.

---

## Conclusion

The **Community.jsx** file is a comprehensive component for displaying community engagement content on a gaming or social platform. It efficiently uses state management, third-party libraries, and services to provide a dynamic and interactive user experience. Through its structured sections, users can view top players, engage with community content, and interact with the platform's social media presence.