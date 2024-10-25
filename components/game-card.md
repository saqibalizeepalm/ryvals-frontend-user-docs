# 🎮 GameCard and GamesList Documentation

Welcome to the documentation of the **GameCard** and **GamesList** components. These components are crafted using **React** and are integral to displaying and interacting with a list of games in a web application.

---

## 📑 Index

1. [GameCard Component](#gamecard-component)
   - [Overview](#overview)
   - [Props](#props)
   - [Usage](#usage)
2. [GamesList Component](#gameslist-component)
   - [Overview](#overview-1)
   - [State Management](#state-management)
   - [Lifecycle Methods](#lifecycle-methods)
   - [Rendering and UI](#rendering-and-ui)
   - [Usage](#usage-1)

---

## 🎴 GameCard Component

### Overview

The **GameCard** component is a functional component designed to display individual game information. It acts as a card that presents a game's image, name, description, and a link to the game's lobby.

### Props

| Prop         | Type     | Description                        |
|--------------|----------|------------------------------------|
| **id**       | number   | Unique identifier of the game.     |
| **name**     | string   | Name of the game.                  |
| **description** | string | Brief description of the game.   |
| **game_type** | string  | Type/category of the game.         |
| **slug**     | string   | URL-friendly name for navigation.  |
| **background_image** | string | URL of the background image. |
| **icon**     | JSX/React Node | Icon representing the game. |

### Usage

```jsx
<GameCard
    id={1}
    name="Chess"
    description="A strategic board game."
    game_type="Board Game"
    slug="chess"
    background_image="path/to/chess.jpg"
    icon={<i className="chess-icon" />}
/>
```

### Key Features

- **Link Navigation**: Each card links to a lobby page for the game using the `slug` prop.
- **Dynamic Styling**: Utilizes `background_image` for an attractive card background.

---

## 🕹️ GamesList Component

### Overview

The **GamesList** component is a class-based component that fetches and displays a list of games. It uses the `GameCard` component to represent each game.

### State Management

The component utilizes `state` to manage:

- **games**: An array of game objects fetched from a service.
- **player_ip**: The IP address of the player, fetched from an external library.
- **isLoading**: A boolean flag to indicate if data is currently being loaded.

### Lifecycle Methods

- **`componentDidMount()`**: 
  - Fetches the list of games using the `gamelisting` service.
  - Sets up event listeners for storage events to handle logouts.
  - Fetches the player's IP address using the `public-ip` library.

### Rendering and UI

The component employs:

- **Parallax Effect**: Adds depth to the game banner using the `react-parallax` library.
- **Conditional Rendering**: Displays a loading spinner while fetching data.
- **Responsive Design**: Utilizes Bootstrap classes for a responsive layout.

### Usage

```jsx
<GamesList />
```

### Key Features

- **Data Fetching**: Retrieves data from a remote source to populate the games list.
- **Player IP Tracking**: Retrieves and stores the player's public IP address.
- **Responsive Slider**: Although commented out, the component has settings for a responsive slider using potential libraries.

---

### 🚀 Conclusion

Both **GameCard** and **GamesList** components are essential for creating an engaging, interactive list of games. By leveraging React's component-based architecture, these components provide flexibility and a clean way to manage and display game data.

If you have any questions or need further assistance, feel free to reach out! Happy coding! 🎉