# CorporateBusiness.jsx Documentation 📄

Welcome to the detailed documentation of the **CorporateBusiness.jsx** file. This file is part of a React-based web application, focusing on rendering a corporate business-themed webpage. Below, we will explore its structure, components, and functionality.

## Table of Contents

1. [Overview](#overview)
2. [Imports](#imports)
3. [Components and State](#components-and-state)
4. [Render Method](#render-method)
5. [Functional Breakdown](#functional-breakdown)
6. [Code Snippets](#code-snippets)

## Overview

The `CorporateBusiness.jsx` file is responsible for setting up a corporate business webpage with various sections like a header, slider, services, team, about, pricing, and more. It leverages several React components to build a modular and reusable UI.

## Imports

The file imports a variety of components and libraries to support its functionality:

- **React Components**: Importing from React and custom components from the project.
- **Modal and Slider**: `react-modal-video` and `react-slick` for enhanced UI interactions.
- **Icons**: From `react-icons/fi` for using Feather icons.
- **Content Components**: Such as `BlogContent`, `Team`, `CounterOne`, and others for dynamic content display.

```jsx
import React, { Component, Fragment } from 'react';
import ModalVideo from 'react-modal-video';
import ScrollToTop from 'react-scroll-up';
import Slider from 'react-slick';
import { slideSlick } from '../page-demo/script';
import BlogContent from '../elements/blog/BlogContent';
import Header from '../component/header/HeaderFive';
import FooterTwo from '../component/footer/FooterTwo';
import CallAction from '../elements/callaction/CallAction';
import Team from '../blocks/team/TeamTwo';
import Accordion01 from '../elements/Accordion';
import Helmet from '../component/common/Helmet';
import {
  FiCast,
  FiLayers,
  FiUsers,
  FiChevronUp,
  FiCheck,
} from 'react-icons/fi';
import CounterOne from '../elements/counters/CounterOne';
import BrandOne from '../elements/Brand';
```

## Components and State

The core class component `CorporateBusiness` extends `React.Component` and manages its state with the following properties:

- **isOpen**: A boolean to control the modal video state.

### Constructor

The constructor initializes the state and binds methods to the component context.

```jsx
constructor() {
    super();
    this.state = { isOpen: false };
    this.openModal = this.openModal.bind(this);
}
```

### openModal Method

A method to set the state of `isOpen` to true, which is used to open a video modal.

```jsx
openModal() {
    this.setState({ isOpen: true });
}
```

## Render Method

The main `render` method is responsible for composing the UI by using various components and passing necessary props.

```jsx
render() {
    ...
    return (
        <Fragment>
            <Helmet pageTitle="Corporate Business" />
            <Header headerPosition="header--static logoresize" logo="all-dark" color="color-black"/>
            {/* Start Slider Area */}
            <div className="slider-wrapper">
                ...
            </div>
            {/* End Slider Area */}
            {/* Start Service Area */}
            <div className="service-area ptb--30 bg_color--1">
                ...
            </div>
            {/* End Service Area */}
            {/* Start Team Area */}
            <div className="rn-team-area ptb--120 bg_color--1">
                ...
            </div>
            {/* End Team Area */}
            <FooterTwo />
            <div className="backto-top">
                <ScrollToTop showUnder={160}>
                    <FiChevronUp />
                </ScrollToTop>
            </div>
        </Fragment>
    );
}
```

## Functional Breakdown

### Header

Uses the `Header` component to set a static header with a logo.

### Slider

Utilizes `Slider` from `react-slick` to create a carousel with slides defined in the `SlideList` array.

### Services Section

Displays a list of services using a mapped array `ServiceListOne` with icons and descriptions.

### Featured Services

Presents a grid of services with images and additional info from the `starndardService` array.

### About Area

Includes an accordion for additional information and a video button to launch a modal video.

### Team

Renders the team members section using the `Team` component with specific column settings.

### Pricing

Showcases different pricing plans with features listed using icons.

### Blog

Displays a set of blog posts from `BlogContent`.

### Call to Action

Incorporates a `CallAction` component for engagement.

### Footer

Includes `FooterTwo` for the footer area of the page.

### Scroll to Top

Implements a smooth scroll to top feature using `ScrollToTop`.

## Code Snippets

Below are some critical snippets to illustrate specific sections:

### Slider Configuration

```jsx
const SlideList = [
    {
        textPosition: 'text-right',
        bgImage: 'bg_image--32',
        category: '',
        title: 'Business.',
        description: 'There are many variations of passages but the majority have suffered alteration.',
        buttonText: 'Contact Us',
        buttonLink: '/contact'
    },
    ...
];
```

### Service List

```jsx
const ServiceListOne = [
    {
        icon: <FiCast />,
        title: 'Business Stratagy',
        description: 'I throw myself down among the tall grass by the stream as I lie close to the earth.'
    },
    ...
];
```

### Pricing Table

```jsx
<div className="rn-pricing">
  <div className="pricing-table-inner">
    <div className="pricing-header">
      <h4 className="title">Free</h4>
      <div className="pricing">
        <span className="price">29</span>
        <span className="subtitle">USD Per Month</span>
      </div>
    </div>
    <div className="pricing-body">
      <ul className="list-style--1">
        <li>
          <FiCheck /> 5 PPC Campaigns
        </li>
        ...
      </ul>
    </div>
    <div className="pricing-footer">
      <a className="rn-btn" href="#pricing">
        Purchase Now
      </a>
    </div>
  </div>
</div>
```

## Conclusion

The `CorporateBusiness.jsx` component is a robust and well-structured React component aimed at presenting a comprehensive corporate business page. It utilizes various components and libraries to deliver a dynamic user interface, providing features like sliders, service listings, team introductions, and more. This modular approach allows for easy maintenance and extension of the page's functionality. 🏢💼
