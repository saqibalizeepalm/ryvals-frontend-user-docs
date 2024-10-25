# 📄 PageNotFound.js Documentation

Welcome to the documentation of the **PageNotFound.js** file. This file is a React component used in web applications to handle scenarios where a user navigates to a non-existent page or an error occurs, potentially indicating that the page could not be found.

This component is also styled to guide users with a message about **deactivating their VPN** and has a cookie consent message. The use of **Parallax** effects adds a visually appealing layer to the component. Below is a detailed breakdown of the file.

## 📑 Index

1. [Overview](#overview)
2. [Imports](#imports)
3. [Component Structure](#component-structure)
   - [Parallax Section](#parallax-section)
   - [Cookies Section](#cookies-section)
4. [Styling](#styling)
5. [License and Usage](#license-and-usage)

## 🌟 Overview

**PageNotFound** is a React component that provides an interactive and visually attractive error page. It utilizes the `Parallax` effect to enhance the visual appeal and displays a message prompting users to deactivate their VPN. Additionally, it includes a section to inform users about the use of cookies, with interactive buttons for consent.

## 📦 Imports

The file imports the following modules:

```javascript
import React, { Component, Fragment } from "react";
import { Parallax } from "react-parallax";
```

- **React**: The core library for building user interfaces.
- **Component** and **Fragment**: Used to define the class-based component and to group multiple elements without adding extra nodes to the DOM.
- **Parallax**: A library that provides a parallax scrolling effect which enhances the user experience with visually appealing backgrounds.

## 🏗️ Component Structure

The `PageNotFound` component is structured into two main sections: 

### 🎨 Parallax Section

This section utilizes the `Parallax` component to create a background with a parallax effect. The purpose is to create an appealing visual experience.

- **Background Image**: `/assets/images/header-background.png`
- **Strength**: The parallax scrolling strength is set to `500`.
- **Class Name**: `page-banner-parallax`

#### HTML Structure:

```jsx
<Parallax bgImage={"/assets/images/header-background.png"} strength={500} bgClassName="page-banner-parallax">
    <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
        <div className="container">
            <div className="row">
                <div className="col-lg-12">
                    <div className="inner text-center">
                        <h1 className="title game-title theme-gradient privacy-policy"> Please Deactivate Your VPN </h1>
                    </div>
                </div>
            </div>
        </div>
    </div>
</Parallax>
```

### 🍪 Cookies Section

This section provides a message about the use of cookies and includes interactive buttons for user consent.

#### HTML Structure:

```jsx
<section className="cookies">
    <div className="container">
        <div className="row">
            <div className="col">
                <p> This website uses cookies <span> We use cookies to personalise content and ads, to provide social media features and to analyse our traffic. We also share information about your use of our site with our social media, advertising and analytics partners who may combine it with other information that you’ve provided to them or that they’ve collected from your use of their services. </span> </p>
                <div className="cookies-buttons">
                    <div><button className="deny-button">Deny</button></div>
                    <div><button className="btn btn-outline-secondary"> Manage </button></div>
                    <div><button className="btn btn-primary">I Accept</button></div>
                </div>
            </div>
        </div>
    </div>
</section>
```

## 🎨 Styling

The component uses various CSS classes to style the elements. Some noticeable classes include:

- **page-banner-parallax**: Styles the background of the parallax section.
- **title**, **game-title**: Used to style the headings with themes and gradients.
- **cookies-buttons**: Styles the cookie consent buttons.

## 📜 License and Usage

This component can be freely used and modified in your projects. Ensure to have the appropriate libraries installed, such as `react-parallax`, to utilize this component effectively.

---

This concludes the documentation for **PageNotFound.js**. By employing parallax effects and engaging cookie sections, this component can greatly enhance the user experience on error or informational pages. Feel free to customize the messages and styles as per your project requirements.