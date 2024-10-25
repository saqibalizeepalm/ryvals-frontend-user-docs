# 📚 Header Components Documentation

This documentation provides a detailed overview of several React components designed to create dynamic headers in a web application. Each component serves to create a navigational header with various styles and functionalities. Below, we will delve into each component one by one.

## Index

1. [HeaderFive.jsx](#headerfivejsx)
2. [Header.jsx](#headerjsx)
3. [HeaderFour.jsx](#headerfourjsx)
4. [HeaderThree.jsx](#headerthreexjsx)
5. [HeaderTwo.jsx](#headertwojsx)

---

## HeaderFive.jsx

### 📄 Overview

The `HeaderFive` component is a React class component that renders a responsive header with a navigation menu. It supports dynamic logo changes based on the properties provided and includes a mobile-friendly hamburger menu.

### ⚙️ Functionalities

- **Menu Toggle**: Allows toggling of the mobile navigation menu.
- **Submenu Toggle**: Enables dropdown and submenu toggle actions.
- **Dynamic Logo**: Changes the logo based on the prop passed, supporting multiple themes (light, dark, symbol variations).
- **Event Listeners**: Attaches listeners to the window for load events.

### 🛠️ Methods

- `menuTrigger()`: Toggles the mobile menu by adding/removing CSS classes.
- `CLoseMenuTrigger()`: Closes the mobile menu by removing CSS classes.

### 🖼️ Usage

```jsx
<HeaderFive logo="dark" color="default-color" headerPosition="fixed" />
```

### 📋 Props

| Prop Name      | Type   | Default Value | Description                                    |
|----------------|--------|---------------|------------------------------------------------|
| `logo`         | String | 'default'     | Determines the logo theme to be displayed.     |
| `color`        | String | 'default'     | Sets the color theme for the header.           |
| `headerPosition` | String | 'static'    | Defines the position of the header (e.g., fixed). |

---

## Header.jsx

### 📄 Overview

The `Header` component is a dynamic and responsive navigation header designed to change its background color on scroll. The header includes a hamburger menu for mobile devices and a logo that can be changed via props.

### ⚙️ Functionalities

- **Scroll Event**: Changes header background when scrolled beyond a certain point.
- **Menu Toggle**: For mobile menu operations.
- **Dynamic Logo**: Supports various logo themes.
- **Navigation Links**: Includes interactive dropdown menus.

### 🛠️ Methods

- `menuTrigger()`: Toggles the mobile menu.
- `CLoseMenuTrigger()`: Closes the mobile menu.
- `listenScrollEvent()`: Updates the header background based on scroll position.

### 🖼️ Usage

```jsx
<Header logo="light" color="transparent" />
```

### 📋 Props

| Prop Name | Type   | Default Value | Description                                  |
|-----------|--------|---------------|----------------------------------------------|
| `logo`    | String | 'default'     | Sets the logo style.                         |
| `color`   | String | 'transparent' | Sets the initial color of the header.        |

--- 

## HeaderFour.jsx

### 📄 Overview

`HeaderFour` is a variation of the header component that presents a flexible navigation bar with dropdown menus and a customizable logo. It is designed to be responsive, ensuring usability on both desktop and mobile devices.

### ⚙️ Functionalities

- **Responsive Design**: Adapts to various screen sizes with a hamburger menu for mobile.
- **Dropdown Menus**: Provides interactive dropdowns for navigation.
- **Dynamic Logo**: Adjusts logo based on theme props.

### 🛠️ Methods

- Similar methods to `HeaderFive` for menu and submenu operations.

### 📋 Props

Refer to `HeaderFive` for similar prop structure.

### 🖼️ Usage

```jsx
<HeaderFour logo="symbol-light" color="default-color" headerPosition="static" />
```

---

## HeaderThree.jsx

### 📄 Overview

The `HeaderThree` component provides a sticky header with integrated social media links. It features a scrolling spy for active navigation and stylish, dynamic logo rendering.

### ⚙️ Functionalities

- **Sticky Header**: Sticks to the top when scrolling past a certain point.
- **Scrollspy**: Highlights current section in navigation as you scroll.
- **Social Media Links**: Includes icons and links to social media platforms.

### 🛠️ Methods

- `menuTrigger()`, `CLoseMenuTrigger()`: For handling mobile menu toggling.
- `stickyHeader()`: (Unused) Intended for sticky header functionality.

### 📋 Props

| Prop Name | Type   | Default Value | Description                                  |
|-----------|--------|---------------|----------------------------------------------|
| `logo`    | String | 'default'     | Sets the logo style.                         |
| `color`   | String | 'default'     | Sets the color theme of the header.          |

### 🖼️ Usage

```jsx
<HeaderThree logo="dark" homeLink="/" />
```

---

## HeaderTwo.jsx

### 📄 Overview

`HeaderTwo` is a versatile component that includes social media links and a comprehensive menu with dropdowns. It's adapted for mobile and desktop views and supports customizable logos.

### ⚙️ Functionalities

- **Menu Interactions**: Dropdowns and submenu functionality.
- **Social Media Integration**: Links to popular social media networks.
- **Responsive Design**: Supports mobile navigation with a hamburger menu.

### 📋 Props

Refer to `Header` and `HeaderFive` for similar prop structures.

### 🖼️ Usage

```jsx
<Header logo="symbol-dark" color="light" />
```

---

### 📚 Conclusion

These header components are designed to enhance the navigational experience of web applications by providing responsive, dynamic, and customizable headers. Each component is tailored to offer different styles and functionalities, making it easier to fit them into various web design requirements. 🖥️✨