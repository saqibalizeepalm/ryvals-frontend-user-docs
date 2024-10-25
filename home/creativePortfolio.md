# 📄 CreativePortfolio.jsx Documentation

Welcome to the documentation for the **CreativePortfolio.jsx** file. This file is responsible for rendering a creative portfolio section of a website using React. Below, you'll find a detailed explanation of its components and functionalities.

---

## 📚 Table of Contents

1. [File Overview](#file-overview)
2. [Components and Imports](#components-and-imports)
3. [PortfolioList Object](#portfoliolist-object)
4. [JSX Structure](#jsx-structure)
5. [External Components and Libraries](#external-components-and-libraries)

---

## 📝 File Overview

This file defines a React component named `CreativePortfolio`. It is a functional component that renders a creative portfolio section, featuring a list of portfolio items. Each item includes an image, category, and title, and links to a detailed portfolio page.

---

## 🔍 Components and Imports

```javascript
import React from 'react';
import ScrollToTop from 'react-scroll-up';
import FooterTwo from "../component/footer/FooterTwo";
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/HeaderFour";
import Helmet from "../component/common/Helmet";
```

The file imports the following components and libraries:

- **React**: Core library for building user interfaces.
- **ScrollToTop**: A component for smooth scrolling to the top of the page.
- **FooterTwo**: A footer component.
- **Header**: A header component that accepts props for styling.
- **Helmet**: A component for managing the document head.
- **FiChevronUp**: An icon from `react-icons` used for the back-to-top button.

---

## 📂 PortfolioList Object

The `PortfolioList` is an array of objects, each representing a portfolio item:

```javascript
const PortfolioList = [
  { images: '9', category: 'Development', title: 'Getting tickets to the big show' },
  { images: '8', category: 'Html', title: 'Getting tickets to the big show' },
  { images: '7', category: 'Graphic', title: 'Getting tickets to the big show' },
  // ... more items
];
```

### Properties

- **images**: Represents the image file number for the portfolio item.
- **category**: The category of the portfolio item (e.g., Development, Html).
- **title**: The title or description of the portfolio item.

---

## ⚙️ JSX Structure

The component returns a JSX structure that builds the portfolio page:

```jsx
<div className="creative-portfolio">
  <Helmet pageTitle="Creative Portfolio" />
  <Header headerPosition="header--static" logo="symbol-dark" color="color-black" />
  <div className="creative-portfolio-wrapper bg_color--1">
    <div className="creative-portfolio-wrapper plr--10">
      <div className="row row--5">
        {PortfolioList.map((value, i) => (
          <div className="col-lg-3 col-md-6 col-12" key={i}>
            <div className="portfolio-style--3">
              <div className="thumbnail">
                <a href="/portfolio-details">
                  <img className="w-100" src={`/assets/images/portfolio/portfolio-${value.images}.jpg`} alt="Portfolio Images" />
                </a>
              </div>
              <div className="content">
                <p className="portfoliotype">{value.category}</p>
                <h4 className="title"><a href="/portfolio-details">{value.title}</a></h4>
                <div className="portfolio-btn">
                  <a className="rn-btn text-white" href="/portfolio-details">Read More</a>
                </div>
              </div>
            </div>
          </div>
        ))}
      </div>
    </div>
  </div>
  <FooterTwo />
  <div className="backto-top">
    <ScrollToTop showUnder={160}>
      <FiChevronUp />
    </ScrollToTop>
  </div>
</div>
```

### Key Features

- **Helmet**: Sets the page title to "Creative Portfolio".
- **Header**: Displays the header with specific styling.
- **Portfolio Items**: Each portfolio item is rendered using data from `PortfolioList`.
- **FooterTwo**: Renders the footer at the bottom of the page.
- **Back to Top**: A button that allows users to scroll back to the top smoothly.

---

## 📦 External Components and Libraries

- **`react-scroll-up`**: Provides functionality to scroll back to the top of the page.
- **`react-icons/fi`**: Provides icon components from the Feather icon set.
- **Custom Components**: `Header`, `FooterTwo`, `Helmet` are custom components presumably defined elsewhere in the project.

---

This concludes the documentation for **CreativePortfolio.jsx**. The file is a well-structured React component that efficiently renders a portfolio section with navigation and smooth scrolling features. This component is integral in showcasing various portfolio items on a website.