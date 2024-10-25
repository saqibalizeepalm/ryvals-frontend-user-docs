# 🎮 Game Lobby Dashboard Documentation

Welcome to the documentation for our **Game Lobby Dashboard**! This documentation will guide you through the various components and functionalities provided in our dashboard. 

## 📋 Index

1. [AvailableLobby.jsx](#availablelobbyjsx)
2. [ActiveLobby.jsx](#activelobbyjsx)
3. [Dashboard.jsx](#dashboardjsx)
4. [Dashboard2.jsx](#dashboard2jsx)
5. [PreviousLobby.jsx](#previouslobbyjsx)

---

## AvailableLobby.jsx

### Overview
The `AvailableLobby` component is a React functional component designed to showcase the available game lobbies. It utilizes several hooks to manage state and side effects and relies on external services for data fetching.

### Key Features
- **Carousel Display**: Uses `react-multi-carousel` to showcase game lobbies in a sliding format.
- **Game Filtering**: Allows filtering of games based on user selection.
- **Loading Spinner**: Displays a spinner while data is being loaded.
- **Lobby Cards**: Each lobby is represented with a card showing relevant game information.

### Code Breakdown

```jsx
import React, { useEffect, useState } from "react";
import { gamelisting } from "../../services/game.service";
import Carousel from "react-multi-carousel";
import "react-multi-carousel/lib/styles.css";
import { callGameFilter } from "../../services/lobbies.service";
import LobbyCard from "../Lobby/LobbyCard";
import { Modal, Spinner } from "react-bootstrap";
```

| Variable | Type | Description |
|----------|------|-------------|
| `gameList` | Array | Stores the list of games fetched from the service. |
| `gameFilter` | Array | Stores filtered games data based on user selection. |
| `spinnerLoadder1` | Boolean | Controls the visibility of the loading spinner. |

### Usage
To display the available lobbies, simply pass the `availableLobbyInfo` prop to the `AvailableLobby` component. This prop contains the list of available lobbies and the loading state.

---

## ActiveLobby.jsx

### Overview
The `ActiveLobby` component is responsible for displaying the currently active game lobbies. It provides detailed information about each lobby, such as entry fees, enrolled players, and the status of the game.

### Key Features
- **Verified Badge**: Displays a badge for verified lobbies.
- **Lobby Details**: Provides comprehensive details about each active lobby.
- **React Tooltip**: Offers additional information on hover using tooltips.
- **Countdown Timer**: Shows a countdown for upcoming lobby events.

### Code Breakdown

```jsx
import React, { useState } from "react";
import { Link } from "react-router-dom";
import CountDown from "../Lobby/CountDown";
import ReactTooltip from "react-tooltip";
import { Modal, Spinner } from "react-bootstrap";
import { modeEnum } from "../../helper/utilities";
```

| Variable | Type | Description |
|----------|------|-------------|
| `isTimerReached` | Boolean | Indicates whether the countdown timer has reached zero. |

### Usage
To render active lobbies, provide the `activeLobbyInfo` prop containing the active lobbies array and the loading state.

---

## Dashboard.jsx

### Overview
The `Dashboard` component serves as the main entry point for navigating through available, active, and previous lobbies. It uses a tabbed interface to switch between different types of lobbies.

### Key Features
- **Tabbed Navigation**: Provides an intuitive tab interface to switch between lobby categories.
- **Parallax Background**: Enhances user experience with a visually appealing parallax effect.
- **Responsive Design**: Adapts to different screen sizes seamlessly.

### Code Breakdown

```jsx
import React, { useEffect, useState } from "react";
import { Parallax } from "react-parallax";
import Tabs from "react-bootstrap/Tabs";
import Tab from "react-bootstrap/Tab";
import ActiveLobby from "./ActiveLobby";
import AvailableLobby from "./AvailableLobby";
import PreviousLobby from "./PreviousLobby";
import { Link } from "react-router-dom";
import { getAvailableLobbies, getActiveLobbies, getPreviousLobbies, } from "../../services/lobbies.service";
```

| Variable | Type | Description |
|----------|------|-------------|
| `key` | String | Tracks the active tab in the dashboard. |
| `availableLobby`, `activeLobby`, `previousLobby` | Array | Store lobby data for each respective category. |

### Usage
Initialize the `Dashboard` component to access all lobby types through a user-friendly interface. Ensure to handle different lobby states for an optimal experience.

---

## Dashboard2.jsx

### Overview
`Dashboard2` extends the functionalities of `Dashboard` by offering more interactive features like redeeming funds and ID verification. It uses a class-based component approach.

### Key Features
- **Modal Popups**: Includes several modals for fund redemption and verification processes.
- **Carousel and Slider**: Displays available lobbies using a `react-slick` slider.
- **Enhanced Interactivity**: Provides functionalities to interact with lobbies and manage user account settings.

### Code Breakdown

```jsx
import React, { Component } from "react";
import { Parallax } from "react-parallax";
import { gameLobbyListing } from "../../services/game.service";
import Tabs from "react-bootstrap/Tabs";
import Tab from "react-bootstrap/Tab";
import Slider from "react-slick";
import { Button, Modal } from "react-bootstrap";
import Form from "react-bootstrap/Form";
```

| Variable | Type | Description |
|----------|------|-------------|
| `lobbies` | Array | Holds the list of game lobbies. |
| `redeemfunds`, `idverification`, `qrverification`, `redeem` | Boolean | Control the visibility of respective modals. |

### Usage
Utilize `Dashboard2` for a more interactive dashboard that supports user account management and detailed lobby interactions.

---

## PreviousLobby.jsx

### Overview
The `PreviousLobby` component displays the user's previously played lobbies, summarizing performance and results for each game session.

### Key Features
- **Detailed Statistics**: Showcases user performance with rankings, kills, and winnings.
- **Verified Status**: Indicates if the lobby was verified.
- **Result Links**: Provides quick access to detailed results of past lobbies.

### Code Breakdown

```jsx
import React from "react";
import { Link } from "react-router-dom";
import { DateFormat } from "../../helper/DateFormatter";
import ReactTooltip from "react-tooltip";
import { Modal, Spinner } from "react-bootstrap";
import { modeEnum } from "../../helper/utilities";
```

| Variable | Type | Description |
|----------|------|-------------|
| `previousLobbyInfo` | Object | Contains an array of past lobbies and loading states. |

### Usage
Integrate `PreviousLobby` into the dashboard to allow users to review their past game performances and extracted insights.

---

**Each component is designed to work together, providing a seamless and engaging user experience for managing and participating in game lobbies. For any customization or additional features, feel free to dive into each component's code!** 🌟

**Note**: Ensure all necessary services are set up for data retrieval and state management to function correctly.