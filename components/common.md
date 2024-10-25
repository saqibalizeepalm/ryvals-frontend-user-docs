# Documentation for React Components

Welcome to the comprehensive documentation for the React components: `Footer.jsx`, `App.jsx`, `Helmet.jsx`, `Header.jsx`, `Logo.jsx`, `List.jsx`, and `Navbar.jsx`. This document provides a detailed breakdown of each component, their purposes, and how they fit into a larger application. This guide is structured using tables, code snippets, and colorful emojis to make it both informative and engaging.

## Index

1. [Footer Component](#footer-component)
2. [App Component](#app-component)
3. [Helmet Component](#helmet-component)
4. [Header Component](#header-component)
5. [Logo Component](#logo-component)
6. [List Component](#list-component)
7. [Navbar Component](#navbar-component)

---

## Footer Component

### Overview

The **Footer** component provides the footer section of a web page, often containing contact information, links, and social media handles. This component is built using React and acts as a static display for various footer-related elements.

### Code Breakdown

```jsx
import React, { Component } from "react";
import { Link } from "react-router-dom";

class Footer extends Component {
  // Constructor with state initialization
  constructor(props) {
    super(props);
    this.state = {
      showPrivacyModal: false,
      termsData: [],
      privacyData: [],
    };
  }

  render() {
    return (
      <>
        <section className="contacts-section">
          {/* Content omitted for brevity */}
        </section>
      </>
    );
  }
}

export default Footer;
```

### Key Features
- **Contact Information**: Displays company contact emails.
- **Quick Links**: Provides easy navigation to important pages such as Discord and FAQ.
- **Social Media Links**: Provides links to various social media platforms.
- **Terms and Policies**: Links to terms and conditions, privacy policy, and brand guidelines.

### Usage
To use the **Footer** component, simply import and include it in your React component tree:
```jsx
import Footer from './Footer';

// In your component's render method
<Footer />
```

---

## App Component

### Overview

The **App** component is the main entry point of the application, responsible for rendering the header, footer, and routing the different pages based on the application's URL.

### Code Breakdown

```jsx
import React, { Component, Fragment } from "react";
import Header from "./Header";
import Footer from "./Footer";
import { Switch, Route } from "react-router-dom";
import { ToastContainer } from "react-toastify";
import { authRoutes, privateRoutes, publicRoutes } from "../../routes/Routes";
import Authmiddleware from "../../routes/AuthMiddleware";
import PageNotFound from "../../component/vpn/PageNotFound";

class App extends Component {
  render() {
    return (
      <Fragment>
        <ToastContainer autoClose={7000} />
        <div className="active-dark">
          <Header logo="symbol-dark" />
          <Switch>
            {publicRoutes.map((route, idx) => (
              <Route exact path={`${process.env.PUBLIC_URL + route.path}`} component={route.component} key={idx} />
            ))}
            {privateRoutes.map((route, idx) => (
              <Authmiddleware path={route.path} component={route.component} key={idx} isAuthProtected={true} />
            ))}
            {authRoutes.map((route, idx) => (
              <Authmiddleware path={route.path} component={route.component} key={idx} isAuthProtected={false} />
            ))}
            <Route component={PageNotFound} />
          </Switch>
          <Footer />
        </div>
      </Fragment>
    );
  }
}

export default App;
```

### Key Features
- **Routing**: Utilizes `react-router-dom` to manage navigation between different components.
- **Header and Footer**: Integrates `Header` and `Footer` components for consistent layout.
- **Toast Notifications**: Uses `react-toastify` for displaying notifications.
- **Authentication**: Implements route protection via `Authmiddleware`.

### Usage
To run the application, ensure that the `App` component is rendered within the `root` of the React application.

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

---

## Helmet Component

### Overview

The **Helmet** component uses `react-helmet` to manage the document head. It dynamically sets the page title and meta descriptions, enhancing SEO and user experience.

### Code Breakdown

```jsx
import React, { Component } from "react";
import { Helmet } from 'react-helmet';

class PageHelmet extends Component {
  render() {
    return (
      <React.Fragment>
        <Helmet>
          <title>{this.props.pageTitle} || React Multipurpose Template</title>
          <meta name="description" content="Trydo – Multipurpose React Template is a multi-use React template." />
        </Helmet>
      </React.Fragment>
    );
  }
}

export default PageHelmet;
```

### Key Features
- **Dynamic Title and Meta Tags**: Changes the document title and meta description based on the `pageTitle` prop.

### Usage
Include the **Helmet** component within the pages where you want to set a custom title and description.

```jsx
import PageHelmet from './Helmet';

function HomePage() {
  return (
    <>
      <PageHelmet pageTitle="Home" />
      {/* Page content */}
    </>
  );
}
```

---

## Header Component

### Overview

The **Header** component provides navigation and branding at the top of the web page, including a logo and navigation menu.

### Code Breakdown

```jsx
import React, { Component } from "react";
import { FiX } from "react-icons/fi";
import HeaderNav from "./Navbar";

class Header extends Component {
  constructor(props) {
    super(props);
    this.menuTrigger = this.menuTrigger.bind(this);
    this.CLoseMenuTrigger = this.CLoseMenuTrigger.bind(this);
  }

  menuTrigger() {
    document.querySelector(".header-wrapper").classList.toggle("menu-open");
  }

  render() {
    return (
      <header className="header-area">
        {/* Header content omitted for brevity */}
      </header>
    );
  }
}

export default Header;
```

### Key Features
- **Responsive Menu**: Toggles menu visibility for mobile.
- **Dynamic Background**: Changes background color on scroll.

### Usage
Simply integrate the **Header** component at the top of your application layout.

```jsx
import Header from './Header';

// In your component's render method
<Header />
```

---

## Logo Component

### Overview

The **Logo** component provides a simple way to display the logo of the application. It uses a `Link` to redirect users to the homepage.

### Code Breakdown

```jsx
import React from "react";
import { Link } from 'react-router-dom';

export const Logo = () => (
  <div className="logo">
    <Link to="/">
      <img src="/assets/images/logo/logo-black.png" alt="Digital Agency" />
    </Link>
  </div>
);
```

### Key Features
- **Clickable Logo**: Redirects to the homepage upon clicking.

### Usage
Can be included wherever a logo is required in the page layout.

```jsx
import { Logo } from './Logo';

// In your component's render method
<Logo />
```

---

## List Component

### Overview

The **List** component is a reusable component that renders a list of business analytics phrases, each prefixed with a check icon.

### Code Breakdown

```jsx
import React, { Component } from "react";
import { FiCheck } from "react-icons/fi";

class ListOne extends Component {
  render() {
    var names = [
      'The Philosophy Of business analytics',
      'Fast-Track Your business',
      'Lies And Damn Lies About business',
      'The Ultimate Deal On business',
    ];
    return (
      <ul className="list-style--1">
        {names.map((name, index) => {
          return <li key={index}><FiCheck /> {name}</li>;
        })}
      </ul>
    );
  }
}

export default ListOne;
```

### Key Features
- **Iconic List**: Each list item is accompanied by a checkmark icon.

### Usage
Integrate the **List** component wherever a stylized list is needed.

```jsx
import ListOne from './List';

// In your component's render method
<ListOne />
```

---

## Navbar Component

### Overview

The **Navbar** component provides navigation options, user authentication actions, and notifications.

### Code Breakdown

```jsx
import React, { useState, useEffect } from "react";
import { Link, useLocation } from "react-router-dom";

const HeaderNav = (props) => {
  const [showNotifications, setShowNotifications] = useState(false);

  const toggleDropDown = () => {
    setShowNotifications((prev) => !prev);
  };

  return (
    <nav className="mainmenunav">
      {/* Navigation content omitted for brevity */}
    </nav>
  );
};

export default HeaderNav;
```

### Key Features
- **User Authentication**: Handles user login/logout and profile navigation.
- **Notification System**: Displays and manages user notifications.
- **Dynamic Navigation**: Adjusts based on user authentication state.

### Usage
Place the **Navbar** component within the `Header` to ensure it remains accessible.

```jsx
import HeaderNav from './Navbar';

// In your component's render method
<HeaderNav />
```

---

This concludes the documentation. Each component is designed to be reusable, modular, and easy to integrate into larger applications. They provide a solid foundation for creating responsive, interactive, and visually appealing web applications. 🎨✨