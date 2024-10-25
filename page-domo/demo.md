# Documentation for `Demo.js` 📜

## Table of Contents 📚

1. [Overview](#overview)
2. [Imports](#imports)
3. [Feature List](#feature-list)
4. [Demo Listings](#demo-listings)
5. [React Component: Demo](#react-component-demo)
6. [Feature Area](#feature-area)
7. [FAQ Section](#faq-section)
8. [Footer and Back To Top](#footer-and-back-to-top)

---

## Overview 🧭

The `Demo.js` file is a React component that serves as a showcase for various templates and demos available in a React-based web application. It primarily uses React components to render a beautiful and interactive UI, allowing users to explore different demos, inner pages, and features of a template called **Trydo**. The file utilizes several libraries to enhance functionality and UI, such as `react-particles-js` for particle animations and `react-tabs` for tabbed content.

---

## Imports 📦

The file imports several libraries and components to aid in its functionality:

- **React Components**: `React`, `Component`, `Fragment`
- **Scroll and Animation**: `react-scroll-up`, `react-particles-js`
- **Icons**: `react-icons/fa`, `react-icons/fi`
- **Accordion**: `react-accessible-accordion`
- **Tabs**: `react-tabs`

```javascript
import React, { Component, Fragment } from "react";
import ScrollToTop from 'react-scroll-up';
import Particles from 'react-particles-js';
import { FaReact, FaSass } from "react-icons/fa";
import { FiSmartphone, FiCode, FiDownload, FiCommand, FiHeadphones, FiBold, FiChevronUp } from "react-icons/fi";
import { Accordion, AccordionItem, AccordionItemHeading, AccordionItemPanel, AccordionItemButton } from 'react-accessible-accordion';
import { Tab, Tabs, TabList, TabPanel } from 'react-tabs';
```

---

## Feature List 🔧

The `featureList` array contains objects detailing the features of the Trydo template. Each feature includes an icon, title, and subtitle.

```javascript
const featureList = [
  { icon: <FaReact/>, title: 'Latest React 16.8+', subtitle: 'We used latest react version ^16.8.6. Its an awesome design made by React.' },
  { icon: <FiSmartphone/>, title: 'Perfect Responsive', subtitle: 'Our Template is fully perfect for all devices. You can visit our template on all devices easily.' },
  { icon: <FiCode/>, title: 'Well Documented Codes', subtitle: 'The Trydo code is well documented and customization is very easy.' },
  // More features...
];
```

---

## Demo Listings 📋

The file contains arrays of objects for different types of demos such as `singleDemo`, `agencyDemo`, `busenessDemo`, `portfolioList`, `landingPage`, `newDemoList`, and `innerDemo`. Each object represents a demo with details like URL, image, title, description, and labels.

### Example of a Demo Object

```javascript
const singleDemo = [
  {
    url: 'main-demo',
    imageUrl: 'demo-home.png',
    title: 'Main Demo',
    description: 'Our Template is perfect for creative agencies. All agencies use this template for all purposes.',
    label: ''
  },
  // More demos...
];
```

---

## React Component: Demo ⚛️

This component renders the Trydo demo showcase. It includes a banner, multiple tabs displaying different demo categories, a feature area, an FAQ section, and a footer.

### Key Parts

- **Banner Area**: Displays the main banner with a logo and purchase links.
- **Tabs**: Uses `react-tabs` to display different categories of demos (e.g., All Demo, Agency, Corporate).
- **Particle Animation**: Uses `react-particles-js` to render a particle effect in the footer.

#### Render Method

```javascript
class Demo extends Component {
  render() {
    return (
      <Fragment>
        {/* Start Banner Area */}
        <div className="prv-banner-wrapper" style={{backgroundImage: `url("assets/images/preview/preview-bg.jpg")`}}>
          {/* Banner Content */}
        </div>

        {/* Start Preview Main Wrapper */}
        <div className="main-wrapper" id="demo">
          {/* Start Main Demo Area */}
          <div className="home-demo-area bg_color--1 ptb--120">
            {/* Tab Panels for Demos */}
          </div>
          {/* End Main Demo Area */}

          {/* Feature Area */}
          {/* FAQ Section */}
          {/* Footer Area */}
        </div>
        {/* End Preview Main Wrapper */}

        {/* Back To Top */}
        <div className="backto-top">
          <ScrollToTop showUnder={160}>
            <FiChevronUp />
          </ScrollToTop>
        </div>
      </Fragment>
    );
  }
}

export default Demo;
```

---

## Feature Area 💡

This section showcases the main features of the Trydo template. It iterates over the `featureList` to display each feature with an icon, title, and description.

```javascript
<div className="prv-feature service-area bg_color--4 ptb--120">
  <div className="wrapper plr--120">
    <div className="row">
      {featureList.map((value, i) => (
        <div className="col-lg-6 col-xl-3 col-md-6 col-sm-6 col-12" key={i}>
          <div className="service service__style--2">
            <div className="icon"> {value.icon} </div>
            <div className="content">
              <h3 className="title">{value.title}</h3>
              <p className="subtitle">{value.subtitle}</p>
            </div>
          </div>
        </div>
      ))}
    </div>
  </div>
</div>
```

---

## FAQ Section ❓

The FAQ section is built using `react-accessible-accordion` to display common questions and answers about the Trydo template. 

```javascript
<div className="pv-feaq-area bg_color--3 ptb--120">
  <div className="container">
    <div className="faq-area">
      <Accordion className="accodion-style--1" preExpanded={'0'}>
        <AccordionItem>
          <AccordionItemHeading>
            <AccordionItemButton> What is tryDo ? How does it work? </AccordionItemButton>
          </AccordionItemHeading>
          <AccordionItemPanel>
            <p>TryDO is a React Creative Agency, React Portfolio and Corporate Multi-Purpose Template...</p>
          </AccordionItemPanel>
        </AccordionItem>
        {/* More Accordion Items */}
      </Accordion>
    </div>
  </div>
</div>
```

---

## Footer and Back To Top 🔝

The footer contains a call-to-action section with background particles for visual appeal. The "Back to Top" functionality is implemented using `react-scroll-up`.

```javascript
<footer className="call-to-action-wrapper text-white-wrapper call-to-action ptb--120 with-particles">
  <div className="frame-layout__particles">
    <Particles params={{ "particles": { "number": { "value": 50 }, "size": { "value": 4 } }, "interactivity": { "events": { "onhover": { "enable": true, "mode": "repulse" } } } }} />
  </div>
  <div className="container">
    <div className="inner text-center">
      <span>Purchase The TryDo and Make Your Site super faster and easy.</span>
      <h2>Let's go to Purchase</h2>
      <a className="rn-button-style--2" href="https://themeforest.net/checkout/from_item/25457315?license=regular"><span>Purchase Now</span></a>
    </div>
  </div>
</footer>
```

---

This documentation provides a comprehensive guide to understanding the `Demo.js` file and its components used to showcase the Trydo template demos and features. 📝