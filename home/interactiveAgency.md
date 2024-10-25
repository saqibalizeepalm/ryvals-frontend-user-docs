# InteractiveAgency.jsx Documentation

## Overview

The **InteractiveAgency.jsx** file is a React component that represents a webpage for an interactive agency. The component is structured to showcase the services provided by the agency, its working process, and other relevant information. The page includes various sections like a slider, about area, services, video modal, and brand area.

### Key Features

- **Slider Area**: Display a full-screen slider with agency information.
- **About Area**: Describe what the agency does and its working process using progress bars.
- **Service Area**: Highlight the services offered by the agency with icons and descriptions.
- **Video Area**: Include a video modal to showcase agency-related content.
- **Brand Area**: Display brand logos or client names.
- **Back to Top**: Enable users to scroll back to the top of the page easily.

## Code Structure

### Imports

```jsx
import React from 'react';
import { ProgressBar } from 'react-bootstrap';
import Helmet from "../component/common/Helmet";
import ScrollToTop from 'react-scroll-up';
import Slider from "react-slick";
import { slideSlick } from "../page-demo/script";
import { FiCast , FiLayers , FiUsers , FiMonitor ,FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import FooterTwo from "../component/footer/FooterTwo";
import VideoModal from "../blocks/VideoModal";
import BrandTwo from "../elements/BrandTwo";
```

### Component Definition

```jsx
const InteractiveAgency = () => {
  return (
    <>
      <Helmet pageTitle="Interactive Agency" />
      <Header />
      ...
      <FooterTwo />
    </>
  );
}
```

### Key Sections

#### 1. **Slider Area**

The slider area is implemented using `react-slick`. It displays slides containing agency information.

```jsx
<div className="slider-wrapper">
  <div className="slider-activation">
    {SlideList.map((value, index) => (
      <div className={`slide slide-style-2 d-flex align-items-center justify-content-center bg_image ${value.bgImage}`} key={index} data-black-overlay="8">
        ...
      </div>
    ))}
  </div>
</div>
```

#### 2. **About Area**

The about area provides an overview of the agency's activities and processes, using progress bars to visualize different aspects like Designing, Management, Marketing, and Development.

```jsx
<div className="rn-about-area ptb--120 bg_color--1">
  <div className="rn-about-wrapper">
    <div className="container">
      ...
      <div className="rn-progress-bar progress-bar--3">
        <div className="single-progress custom-color--1">
          <h6 className="title">Designing</h6>
          <ProgressBar now={81} />
          <span className="label">81%</span>
        </div>
        ...
      </div>
    </div>
  </div>
</div>
```

#### 3. **Service Area**

Displays a list of services with icons and descriptions.

```jsx
<div className="service-area creative-service-wrapper pb--120 bg_color--1">
  <div className="container">
    ...
    <div className="row creative-service">
      {ServiceList.map((val, i) => (
        <div className="col-xl-4 col-lg-4 col-md-6 col-sm-6 col-12" key={i}>
          <a className="text-center" href="/service-details">
            <div className="service service__style--2">
              <div className="icon"> {val.icon} </div>
              <div className="content">
                <h3 className="title">{val.title}</h3>
                <p>{val.description}</p>
              </div>
            </div>
          </a>
        </div>
      ))}
    </div>
  </div>
</div>
```

#### 4. **Video Area**

Includes a section for a video modal that can display a video related to the agency's services or projects.

```jsx
<div className="rn-section pb--120 bg_color--1">
  <div className="container">
    ...
    <VideoModal />
  </div>
</div>
```

#### 5. **Brand Area**

Showcases the brands or clients associated with the agency.

```jsx
<div className="rn-brand-area pb--120 bg_color--1">
  <div className="container">
    <BrandTwo />
  </div>
</div>
```

#### 6. **Back To Top**

A button to allow users to scroll back to the top of the page.

```jsx
<div className="backto-top">
  <ScrollToTop showUnder={160}>
    <FiChevronUp />
  </ScrollToTop>
</div>
```

## Conclusion

The **InteractiveAgency.jsx** component is a comprehensive React component designed to represent an agency's landing page. It contains essential sections to engage users and provide relevant information about the agency's services and projects. By leveraging third-party libraries like `react-slick`, `react-bootstrap`, and icons from `react-icons`, the component provides a modern and interactive user experience.