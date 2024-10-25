# ManageCookies.jsx Documentation

## Overview

The `ManageCookies.jsx` component is a React component that allows users to manage their cookie preferences on a website. It utilizes React hooks for state management and the `js-cookie` library to handle cookies. The component presents a form where users can select different types of cookies they wish to enable or disable, and then submit their preferences.

---

## Table of Contents

1. [Imports](#imports)
2. [State Management](#state-management)
3. [Effects](#effects)
4. [Event Handlers](#event-handlers)
5. [Rendering](#rendering)
6. [Usage](#usage)

---

### Imports

```javascript
import React, { useState, useEffect } from "react";
import { Parallax } from "react-parallax";
import Form from "react-bootstrap/Form";
import Button from "react-bootstrap/Button";
import Cookies from "js-cookie";
```

- **React, useState, useEffect**: Core React library and hooks for managing component state and lifecycle.
- **Parallax**: Used for creating a parallax scrolling effect in the page header.
- **Form, Button**: Components from `react-bootstrap` for creating forms and buttons.
- **Cookies**: A utility from `js-cookie` for handling cookies in the browser.

---

### State Management

The component uses React's `useState` hook to manage four pieces of state, corresponding to different cookie preferences:

```javascript
const [first, setFirst] = useState(false);
const [second, setSecond] = useState(true);
const [third, setThird] = useState(true);
const [fourth, setFourth] = useState(true);
```

- **first**: Manages the state of essential cookies.
- **second**: Manages the state of analytical/performance cookies.
- **third**: Manages the state of targeting/advertising cookies.
- **fourth**: Manages the state of third-party cookies.

---

### Effects

The `useEffect` hook is used to initialize the state from stored cookie values when the component mounts:

```javascript
useEffect(() => {
  setFirst(Cookies.get("first") === "false" || Cookies.get("first") === undefined ? false : true);
  setSecond(Cookies.get("second") === "false" ? false : true);
  setThird(Cookies.get("third") === "false" ? false : true);
  setFourth(Cookies.get("fourth") === "false" ? false : true);
}, []);
```

This effect reads the current cookie settings when the component mounts and updates the state accordingly.

---

### Event Handlers

Each checkbox in the form is associated with an event handler that updates the corresponding state and sets the cookie value:

```javascript
const onChangeFirst = (e) => {
  const check = e.target.checked;
  Cookies.set("first", check);
  setFirst(check);
};

const onChangeSecond = (e) => {
  const check = e.target.checked;
  Cookies.set("second", check);
  setSecond(check);
};

const onChangeThird = (e) => {
  const check = e.target.checked;
  Cookies.set("third", check);
  setThird(check);
};

const onChangeFourth = (e) => {
  const check = e.target.checked;
  Cookies.set("fourth", check);
  setFourth(check);
};
```

The `handleSubmit` function finalizes the changes and redirects the user:

```javascript
const handleSubmit = () => {
  Cookies.set("Accept", "true", { expires: 62 });
  window.location.replace("/home");
};
```

---

### Rendering

The component renders a form within a parallax section. The form includes:

- Checkboxes for each type of cookie preference.
- Descriptions for each cookie type.
- A submit button to save preferences.

```jsx
return (
  <>
    <div className="slider-activation slider-creative-agency profile-slider">
      <Parallax bgImage={"/assets/images/header-background.png"} strength={500} bgClassName="page-banner-parallax profile-banner-parallax" >
        <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="inner text-center">
                  <h1 className="title game-title theme-gradient">Cookies</h1>
                </div>
              </div>
            </div>
          </div>
        </div>
      </Parallax>
    </div>
    <section class="manage-cookies">
      <div class="container">
        <div class="row">
          <div class="col">
            <p> Cookies are small amounts of data stored in separate files within your computer's internet browser...</p>
            <div>
              <Form>
                <Form.Group className="check-wrapper" controlId="formBasicCheckbox">
                  <Form.Check type="checkbox" label="Essential" onChange={onChangeFirst} checked={first} />
                  <p> These are cookies that are required for the operation of our website...</p>
                </Form.Group>
                {/* Additional Form.Group components for second, third, and fourth cookies */}
                <Button variant="primary" type="button" onClick={handleSubmit}> Submit </Button>
              </Form>
            </div>
          </div>
        </div>
      </div>
    </section>
  </>
);
```

---

### Usage

To use the `ManageCookies` component:

1. Import it into your application.
2. Include it wherever you need to provide users with cookie management options.

```jsx
import ManageCookies from './path/to/ManageCookies.jsx';

// Usage
<ManageCookies />
```

This component is typically used in applications that need to comply with privacy regulations by providing users with control over tracking and advertising technologies.