# PortfolioLanding.jsx Documentation

Welcome to the detailed documentation for the `PortfolioLanding.jsx` file! This component is designed to showcase a portfolio landing page with a beautiful UI and various sections such as About, Services, Portfolio, Blog, and Contact.

## Table of Contents

- [Overview](#overview)
- [Component Structure](#component-structure)
- [Key Features](#key-features)
- [Code Breakdown](#code-breakdown)
- [Usage](#usage)
- [Dependencies](#dependencies)

## Overview

The `PortfolioLanding.jsx` is a React functional component that represents a portfolio landing page. It includes sections like About Me, Services, Portfolio, Blog, and Contact, providing a comprehensive showcase of a personal or agency portfolio.

## Component Structure

```plaintext
PortfolioLanding
├── Helmet
├── HeaderThree
├── Slider Area
├── About Area
├── Service Area
├── Portfolio Area
├── Blog Area
├── Contact Area
└── FooterTwo
```

## Key Features

- **Responsive Design**: The component is designed to provide a seamless experience across different screen sizes.
- **Slider**: A dynamic slider to highlight key aspects of the portfolio.
- **About Section**: A customizable section to describe the portfolio owner.
- **Service Listing**: Display the services offered with a neat layout.
- **Portfolio Showcase**: Present the most recent projects in a visually appealing manner.
- **Blog Section**: Showcase the latest blog posts or news.
- **Contact Form**: A contact area to facilitate communication.
- **Scroll-To-Top Button**: Enhances navigation by allowing quick access to the top of the page.

## Code Breakdown

Here's a detailed explanation of the component's code:

### Imports

```javascript
import React from 'react';
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import HeaderThree from "../component/header/HeaderThree";
import FooterTwo from "../component/footer/FooterTwo";
import TabTwo from "../elements/tab/TabTwo";
import ContactOne from "../elements/contact/ContactOne";
import PortfolioList from "../elements/portfolio/PortfolioList";
import ServiceList from "../elements/service/ServiceList";
import BlogContent from "../elements/blog/BlogContent";
import Helmet from "../component/common/Helmet";
```

- **React**: The core library for building user interfaces.
- **ScrollToTop**: Component for scrolling back to the top of the page.
- **FiChevronUp**: An icon used for the scroll-to-top button.
- **Various Custom Components**: These are imported to structure the landing page, including header, footer, portfolio, services, and more.

### Slide List

```javascript
const SlideList = [
  {
    textPosition: 'text-left',
    category: 'Freelance digital designer',
    title: 'Hello, I’m <span>Nancy</span> Welcome to my World.',
    description: '',
    buttonText: '',
    buttonLink: ''
  }
];
```

- **SlideList**: An array of objects used to configure the slider section.

### Main Component

```javascript
const PortfolioLanding = () => {
  let title = 'About Me', description = 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered <a href="#">alteration</a> in some form, by injected humour, or randomised words which dont look even slightly believable. If you are going to use a passage of Lorem Ipsum,';
  const PostList = BlogContent.slice(0, 3);

  return (
    <div>
      <Helmet pageTitle="Portfolio Landing" />
      <HeaderThree homeLink="/" logo="symbol-dark" color="color-black"/>
      
      {/* Slider Area */}
      <div id="home" className="fix">
        <div className="slider-wrapper">
          {SlideList.map((value, index) => (
            <div className="slide personal-portfolio-slider slider-paralax slider-style-3 d-flex align-items-center justify-content-center bg_image bg_image--25" key={index}>
              <div className="container">
                <div className="row">
                  <div className="col-lg-12">
                    <div className={`inner ${value.textPosition}`}>
                      {value.category ? <span>{value.category}</span> : ''}
                      {value.title ? <h1 className="title" dangerouslySetInnerHTML={{__html: value.title}}></h1> : ''}
                      {value.description ? <p className="description">{value.description}</p> : ''}
                      {value.buttonText ? <div className="slide-btn"><a className="rn-button-style--2 btn-primary-color" href={`${value.buttonLink}`}>{value.buttonText}</a></div> : ''}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
      
      {/* About Area */}
      <div id="about" className="fix">
        <div className="about-area ptb--120 bg_color--1">
          <div className="about-wrapper">
            <div className="container">
              <div className="row row--35 align-items-center">
                <div className="col-lg-5">
                  <div className="thumbnail">
                    <img className="w-100" src="/assets/images/about/about-7.jpg" alt="About Images"/>
                  </div>
                </div>
                <div className="col-lg-7">
                  <div className="about-inner inner">
                    <div className="section-title">
                      <h2 className="title">{title}</h2>
                      <p className="description">{description}</p>
                    </div>
                    <div className="row mt--30">
                      <TabTwo tabStyle="tab-style--1" />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Service Area */}
      <div id="service" className="fix">
        <div className="service-area creative-service-wrapper ptb--120 bg_color--5">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="section-title text-center service-style--3 mb--30 mb_sm--0">
                  <h2 className="title">My Awesome Service</h2>
                  <p>There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration.</p>
                </div>
              </div>
            </div>
            <div className="row creative-service">
              <div className="col-lg-12">
                <ServiceList item="6" column="col-lg-4 col-md-6 col-sm-6 col-12 text-left" />
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Portfolio Area */}
      <div id="portfolio" className="fix">
        <div className="portfolio-area ptb--120 bg_color--1">
          <div className="portfolio-sacousel-inner">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="section-title text-center service-style--3 mb--30 mb_sm--0">
                    <h2 className="title">My Latest Project</h2>
                    <p>There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration.</p>
                  </div>
                </div>
              </div>
              <div className="row">
                <PortfolioList styevariation="text-center mt--40" column="col-lg-4 col-md-6 col-sm-6 col-12" item="6" />
              </div>
              <div className="row">
                <div className="col-lg-12">
                  <div className="view-more-btn mt--60 mt_sm--30 text-center">
                    <a className="rn-button-style--2 btn-solid" href="/blog"><span>View More</span></a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Blog Area */}
      <div id="blog" className="fix">
        <div className="rn-blog-area ptb--120 bg_color--5 mb-dec--30">
          <div className="container">
            <div className="row align-items-end">
              <div className="col-lg-12 col-md-12 col-sm-12 col-12">
                <div className="section-title text-center">
                  <h2>Latest News</h2>
                  <p>There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration.</p>
                </div>
              </div>
            </div>
            <div className="row mt--60 mt_sm--40">
              {PostList.map((value, i) => (
                <div className="col-lg-4 col-md-6 col-12" key={i}>
                  <div className="blog blog-style--1">
                    <div className="thumbnail">
                      <a href="/blog-details">
                        <img className="w-100" src={`/assets/images/blog/blog-${value.images}.jpg`} alt="Blog Images"/>
                      </a>
                    </div>
                    <div className="content">
                      <p className="blogtype">{value.category}</p>
                      <h4 className="title"><a href="/blog-details">{value.title}</a></h4>
                      <div className="blog-btn">
                        <a className="rn-btn text-white" href="/blog-details">Read More</a>
                      </div>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>
        </div>
      </div>

      {/* Contact Area */}
      <div id="contact" className="fix">
        <div className="rn-contact-area ptb--120 bg_color--1">
          <ContactOne />
        </div>
      </div>

      <FooterTwo />

      {/* Back To Top */}
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
    </div>
  )
}
export default PortfolioLanding;
```

## Usage

To make use of the `PortfolioLanding` component, make sure to import and render it within a parent component or directly in your application's entry point.

## Dependencies

- **React**: JavaScript library for building user interfaces.
- **react-scroll-up**: For creating a scroll-to-top button.
- **react-icons**: For icon components.
- **Custom Components**: Make sure all referenced components like `HeaderThree`, `FooterTwo`, `ServiceList`, etc., are correctly implemented and imported.

---

This documentation should serve as a comprehensive guide to understanding and utilizing the `PortfolioLanding.jsx` component. Happy coding! 🚀