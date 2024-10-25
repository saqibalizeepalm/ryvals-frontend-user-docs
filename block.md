# Documentation for React Components

Welcome to the comprehensive documentation for the React components! 🌟 This documentation will provide detailed insights into each component, explaining their purpose, usage, and structure.

## Index

1. [Brand.jsx](#1-brandjsx)
2. [Columns.jsx](#2-columnsjsx)
3. [Counters.jsx](#3-countersjsx)
4. [ContactForm.jsx](#4-contactformjsx)
5. [Elements.jsx](#5-elementsjsx)
6. [Gallery.jsx](#6-galleryjsx)
7. [Portfolio.jsx](#7-portfoliojsx)
8. [GoogleMap.jsx](#8-googlemapjsx)
9. [ProgressBar.jsx](#9-progressbarjsx)
10. [PricingTable.jsx](#10-pricingtablejsx)
11. [Testimonial.jsx](#11-testimonialjsx)
12. [Team.jsx](#12-teamjsx)
13. [VideoPopup.jsx](#13-videopopupjsx)
14. [VideoModal.jsx](#14-videomodaljsx)
15. [ProgressTwo.jsx](#15-progresstwojsx)
16. [ProgressOne.jsx](#16-progressonejsx)
17. [TeamOne.jsx](#17-teamonexjsx)
18. [data.jsx](#18-datajsx)
19. [TeamTwo.jsx](#19-teamtwoxjsx)
20. [TestimonialTwo.jsx](#20-testimonialtwoxjsx)
21. [TestimonialOne.jsx](#21-testimonialonexjsx)

---

### 1. Brand.jsx

**Purpose**: This component is used to display brand logos in a designated area of a webpage. It supports two styles of brand displays (`BrandOne` and `BrandTwo`).

**Key Features**:
- **Helmet** for setting the page title.
- **Breadcrumb** for navigation.
- Supports a back-to-top button using `react-scroll-up`.
- Two brand display sections with different styles.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";
import BrandOne from "../elements/Brand";
import BrandTwo from "../elements/BrandTwo";

const Brand = () => {
  return (
    <>
      <PageHelmet pageTitle='Client Logo' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Client Logo'} />
      <main className="page-wrapper">
        <div className="rn-brand-area ptb--120 bg_color--5">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <BrandOne branstyle="branstyle--2" />
              </div>
            </div>
          </div>
        </div>
        <div className="rn-brand-area brand-separation bg_color--1">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <BrandTwo />
              </div>
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Brand;
```

---

### 2. Columns.jsx

**Purpose**: This component demonstrates different column layouts, showcasing one full column, two half columns, and three third columns, each with different design styles.

**Key Features**:
- **Helmet** and **Breadcrumb** for page metadata and navigation.
- Various column-based layouts for content display.
- Utilizes **Lorem Ipsum** for placeholder text.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";

const Columns = () => {
  return (
    <>
      <PageHelmet pageTitle='Columns' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Columns'} />
      <main className="page-wrapper">
        <div className="rn-columns-area ptb--120 bg_color--5">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="single-column">
                  <h4 className="tilte">One Full</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div className="rn-columns-area ptb--120 bg_color--1">
          <div className="container">
            <div className="row">
              <div className="col-lg-6 col-md-6 col-12">
                <div className="single-column">
                  <h4 className="tilte">One Half</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
              <div className="col-lg-6 col-md-6 col-12 mt_sm--30">
                <div className="single-column">
                  <h4 className="tilte">One Half</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div className="rn-columns-area ptb--120 bg_color--5">
          <div className="container">
            <div className="row">
              <div className="col-lg-4 col-md-6 col-12">
                <div className="single-column">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12 mt_sm--30">
                <div className="single-column">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12 mt_sm--30 mt_md--30">
                <div className="single-column">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div className="rn-columns-area ptb--120 bg_color--1">
          <div className="container">
            <div className="row">
              <div className="col-lg-4 col-md-6 col-12">
                <div className="single-column custom-color">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12 mt_sm--30">
                <div className="single-column custom-color custom-color--1">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12 mt_sm--30 mt_md--30">
                <div className="single-column custom-color custom-color--2">
                  <h4 className="tilte">One Third</h4>
                  <p>There are many variations of passages of Lorem Ipsum...</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Columns;
```

---

### 3. Counters.jsx

**Purpose**: This component showcases counter elements, employing two different counter styles (`CounterOne` and `CounterTwo`).

**Key Features**:
- **Helmet** and **Breadcrumb** for page navigation and metadata.
- Displays counters in different themed areas.
- Supports a back-to-top button.

```jsx
import React from 'react';
import TeamOne from "./team/TeamOne";
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import CounterOne from "../elements/counters/CounterOne";
import CounterTwo from "../elements/counters/CounterTwo";
import Footer from "../component/footer/Footer";

const Counters = () => {
  return (
    <>
      <PageHelmet pageTitle='Counters' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Counters'} />
      <main className="page-wrapper">
        <div className="counterup-area ptb--120 bg_color--1">
          <div className="container">
            <CounterOne />
          </div>
        </div>
        <div className="counterup-area ptb--120 bg-theme-gradient theme-text-white">
          <div className="container">
            <CounterOne />
          </div>
        </div>
        <div className="counterup-area ptb--120 bg_color--1">
          <div className="container">
            <CounterTwo />
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Counters;
```

---

### 4. ContactForm.jsx

**Purpose**: This component renders a contact form section, allowing users to get in touch via a form integrated on the page.

**Key Features**:
- **Helmet** and **Breadcrumb** for navigation and metadata.
- Incorporates the `ContactThree` component to display the form.
- Includes a back-to-top button for user convenience.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";
import ContactThree from "../elements/contact/ContactThree";

const ContactForm = () => {
  return (
    <>
      <PageHelmet pageTitle='Contact Form' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Contact Form'} />
      <main className="page-wrapper">
        <div className="rn-contact-form-area ptb--120 bg_color--1">
          <ContactThree contactTitle="Contact Us" contactImages="/assets/images/about/about-6.jpg" />
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default ContactForm;
```

---

### 5. Elements.jsx

**Purpose**: A placeholder component, likely designed for future content or component integrations.

**Key Features**:
- Basic structure with **Helmet** and **Breadcrumb**.
- Empty page wrapper that can be utilized for additional elements.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";

const Elements = () => {
  return (
    <>
      <PageHelmet pageTitle='Counters' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Counters'} />
      <main className="page-wrapper">
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Elements;
```

---

### 6. Gallery.jsx

**Purpose**: Renders a gallery section with lightbox functionality that allows users to view images in a modal.

**Key Features**:
- Integrates `react-image-lightbox` for enhanced image viewing.
- Displays a portfolio of images with categories and titles.
- Includes a back-to-top feature.

```jsx
import React, { Component } from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/FooterTwo";
import Lightbox from 'react-image-lightbox';
import 'react-image-lightbox/style.css';

const PortfolioList = [/* Portfolio items */];
const TabOne = [/* Tab items */];

class Gallery extends Component {
  constructor(props) {
    super(props);
    this.state = {
      tab1: 0,
      isOpen: false,
    };
  }

  render() {
    const { tab1, isOpen } = this.state;
    return (
      <div>
        <PageHelmet pageTitle='Gallery' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Gallery'} />
        <main className="page-wrapper">
          <div className="rn-portfolio-area ptb--120 bg_color--1 line-separator">
            <div className="container">
              <div className="row">
                {TabOne.map((value, index) => (
                  <div className="col-lg-6" key={index}>
                    {isOpen && (
                      <Lightbox
                        mainSrc={TabOne[tab1].bigImage}
                        nextSrc={TabOne[(tab1 + 1) % TabOne.length]}
                        prevSrc={TabOne[(tab1 + TabOne.length - 1) % TabOne.length]}
                        onCloseRequest={() => this.setState({ isOpen: false })}
                        onMovePrevRequest={() =>
                          this.setState({
                            tab1: (tab1 + TabOne.length - 1) % TabOne.length,
                          })
                        }
                        onMoveNextRequest={() =>
                          this.setState({
                            tab1: (tab1 + 1) % TabOne.length,
                          })
                        }
                      />
                    )}
                    <div className="item-portfolio-static">
                      <div onClick={() => this.setState({ isOpen: true, tab1: index })}>
                        <div className="portfolio-static">
                          <div className="thumbnail-inner">
                            <div className="thumbnail">
                              <a href="#portfolio-details">
                                <img
                                  src={`/assets/images/portfolio/dp-portfolio-${value.image}.jpg`}
                                  alt="Portfolio Images"
                                />
                              </a>
                            </div>
                          </div>
                          <div className="content">
                            <div className="inner">
                              <p>{value.category}</p>
                              <h4>
                                <a href="#portfolio-details">{value.title}</a>
                              </h4>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
          <div className="creative-portfolio-wrapper ptb--120 bg_color--1">
            <div className="container plr--10">
              <div className="row row--5">
                {PortfolioList.map((value, i) => (
                  <div className="col-lg-4 col-md-6 col-12" key={i}>
                    <div className="portfolio-style--3">
                      <div className="thumbnail">
                        <a href="/portfolio-details">
                          <img
                            className="w-100"
                            src={`/assets/images/portfolio/portfolio-${value.images}.jpg`}
                            alt="Portfolio Images"
                          />
                        </a>
                      </div>
                      <div className="content">
                        <p className="portfoliotype">{value.category}</p>
                        <h4 className="title">
                          <a href="/portfolio-details">{value.title}</a>
                        </h4>
                        <div className="portfolio-btn">
                          <a className="rn-btn text-white" href="/portfolio-details">
                            Read More
                          </a>
                        </div>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        </main>
        <div className="backto-top">
          <ScrollToTop showUnder={160}>
            <FiChevronUp />
          </ScrollToTop>
        </div>
        <Footer />
      </div>
    );
  }
}

export default Gallery;
```

---

### 7. Portfolio.jsx

**Purpose**: Displays a portfolio section with different layouts, including sliders for enhanced navigation through portfolio items.

**Key Features**:
- Integrates `react-slick` for sliding functionality.
- Showcases the portfolio in different themed areas.
- Back-to-top button for easy navigation.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";
import Slider from "react-slick";
import PortfolioList from "../elements/portfolio/PortfolioList";
import { slickDot, portfolioSlick2 } from "../page-demo/script";

const list = [/* Portfolio items */];
const PortfolioList2 = [/* Portfolio items */];

const Portfolio = () => {
  return (
    <>
      <PageHelmet pageTitle='Counters' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Portfolio'} />
      <main className="page-wrapper">
        <div className="portfolio-area pt--90 pb--140 bg_color--1">
          <div className="rn-slick-dot">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="slick-space-gutter--15 slickdot--20">
                    <Slider {...slickDot}>
                      {list.map((value, index) => (
                        <div className="portfolio" key={index}>
                          <div className="thumbnail-inner">
                            <div className={`thumbnail ${value.image}`}></div>
                            <div className={`bg-blr-image ${value.image}`}></div>
                          </div>
                          <div className="content">
                            <div className="inner">
                              <p>{value.category}</p>
                              <h4>
                                <a href="/portfolio-details">{value.title}</a>
                              </h4>
                              <div className="portfolio-button">
                                <a className="rn-btn" href="/portfolio-details">
                                  Case Study
                                </a>
                              </div>
                            </div>
                          </div>
                        </div>
                      ))}
                    </Slider>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div className="portfolio-area ptb--120 bg_color--5">
          <div className="portfolio-sacousel-inner">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="section-title text-center service-style--3 mb--30">
                    <h2 className="title">All Works</h2>
                    <p>There are many variations of passages of Lorem Ipsum available...</p>
                  </div>
                </div>
              </div>
              <div className="row">
                <PortfolioList styevariation="text-left mt--40" column="col-lg-4 col-md-6 col-sm-6 col-12" item="6" />
              </div>
              <div className="row">
                <div className="col-lg-12">
                  <div className="view-more-btn mt--60 text-center">
                    <a className="rn-button-style--2 btn-solid" href="/portfolio">
                      <span>View More Project</span>
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div className="portfolio-area ptb--120 bg_color--1">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="section-title text-center service-style--3 mb--30">
                  <h2 className="title">All Works</h2>
                  <p>There are many variations of passages of Lorem Ipsum available...</p>
                </div>
              </div>
            </div>
            <div className="wrapper portfolio-sacousel-inner mb--55">
              <div className="portfolio-slick-activation mt--70 mt_sm--40">
                <Slider {...portfolioSlick2}>
                  {PortfolioList2.map((value, index) => (
                    <div className="portfolio" key={index}>
                      <div className="thumbnail-inner">
                        <div className={`thumbnail ${value.image}`}></div>
                        <div className={`bg-blr-image ${value.image}`}></div>
                      </div>
                      <div className="content">
                        <div className="inner">
                          <p>{value.category}</p>
                          <h4>
                            <a href="/portfolio-details">{value.title}</a>
                          </h4>
                          <div className="portfolio-button">
                            <a className="rn-btn" href="/portfolio-details">
                              Case Study
                            </a>
                          </div>
                        </div>
                      </div>
                    </div>
                  ))}
                </Slider>
              </div>
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  );
}

export default Portfolio;
```

---

### 8. GoogleMap.jsx

**Purpose**: Renders a Google Map on the page, displaying a specific location with a marker.

**Key Features**:
- Utilizes `google-map-react` to integrate Google Maps.
- Displays multiple map instances with different layouts.
- Includes a back-to-top button for ease of navigation.

```jsx
import React, { Component } from 'react';
import GoogleMapReact from 'google-map-react';
import { FiChevronUp } from "react-icons/fi";
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";

const AnyReactComponent = ({ text }) => <div>{text}</div>;

class GoogleMap extends Component {
  static defaultProps = {
    center: { lat: 59.95, lng: 30.33 },
    zoom: 11
  };

  render() {
    return (
      <>
        <PageHelmet pageTitle='Google Map' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Google Map'} />
        <main className="page-wrapper">
          <div className="rn-contact-map-wrapper ptb--120 bg_color--1">
            <div className="container">
              <div className="row">
                <div className="col-lg-6">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
                <div className="col-lg-6">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="rn-contact-map-wrapper ptb--120 bg_color--5">
            <div className="container">
              <div className="row">
                <div className="col-lg-4 col-md-6 col-12">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
                <div className="col-lg-4 col-md-6 col-12 mt_sm--30">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
                <div className="col-lg-4 col-md-6 col-12 mt_md--30 mt_sm--30">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="rn-contact-map-wrapper ptb--120 bg_color--1">
            <div className="container">
              <div className="row">
                <div className="col-lg-12 col-12">
                  <div className="rn-contact-map-area position-relative">
                    <div style={{ height: '550px', width: '100%' }}>
                      <GoogleMapReact
                        defaultCenter={this.props.center}
                        defaultZoom={this.props.zoom}
                      >
                        <AnyReactComponent lat={59.955413} lng={30.337844} text="My Marker" />
                      </GoogleMapReact>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </main>
        <div className="backto-top">
          <ScrollToTop showUnder={160}>
            <FiChevronUp />
          </ScrollToTop>
        </div>
        <Footer />
      </>
    )
  }
}

export default GoogleMap;
```

---

### 9. ProgressBar.jsx

**Purpose**: Displays progress bars for different skills or tasks, using two types of progress bars (`ProgressOne` and `ProgressTwo`).

**Key Features**:
- **Helmet** and **Breadcrumb** for metadata and navigation.
- Utilizes `react-bootstrap` for progress bar components.
- Multiple progress areas to show different progress styles.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import ProgressOne from "./progressbar/ProgressOne";
import ProgressTwo from "./progressbar/ProgressTwo";
import Footer from "../component/footer/Footer";

const ProgressBar = () => {
  return (
    <>
      <PageHelmet pageTitle='Progress Bar' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Progress Bar'} />
      <main className="page-wrapper">
        <div className="rn-progress-area ptb--120 bg_color--1">
          <div className="container">
            <div className="row row--35">
              <div className="col-lg-6 col-md-6 col-12">
                <ProgressOne ProgressStyle="progress-bar--1" />
              </div>
              <div className="col-lg-6 col-md-6 col-12 mt_sm--30">
                <ProgressOne ProgressStyle="progress-bar--2" />
              </div>
            </div>
          </div>
        </div>
        <div className="rn-progress-area pb--120 bg_color--1">
          <div className="container">
            <div className="row row--35">
              <div className="col-lg-6 col-md-6 col-12">
                <ProgressOne ProgressStyle="progress-bar--3" />
              </div>
              <div className="col-lg-6 col-md-6 col-12 mt_sm--30">
                <ProgressTwo ProgressStyle="" />
              </div>
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default ProgressBar;
```

---

### 10. PricingTable.jsx

**Purpose**: Renders a pricing table with different pricing tiers, each with its own set of features and pricing details.

**Key Features**:
- **Helmet** and **Breadcrumb** for navigation and metadata.
- Displays three pricing tiers: Free, Business, and Advanced.
- Each tier includes a list of features and a purchase button.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp, FiCheck } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";

const PricingTable = () => {
  return (
    <>
      <PageHelmet pageTitle='Pricing Table' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Pricing Table'} />
      <main className="page-wrapper">
        <div className="rn-pricing-table-area ptb--120 bg_color--5">
          <div className="container">
            <div className="row">
              <div className="col-lg-4 col-md-6 col-12">
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
                        <li><FiCheck /> 5 PPC Campaigns</li>
                        <li><FiCheck /> Digital Marketing</li>
                        <li><FiCheck /> Marketing Agency</li>
                        <li><FiCheck /> Seo Friendly</li>
                        <li><FiCheck /> UI/UX designs</li>
                      </ul>
                    </div>
                    <div className="pricing-footer">
                      <a className="rn-btn" href="#pricing">Purchase Now</a>
                    </div>
                  </div>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12">
                <div className="rn-pricing active">
                  <div className="pricing-table-inner">
                    <div className="pricing-header">
                      <h4 className="title">Business</h4>
                      <div className="pricing">
                        <span className="price">29</span>
                        <span className="subtitle">USD Per Month</span>
                      </div>
                    </div>
                    <div className="pricing-body">
                      <ul className="list-style--1">
                        <li><FiCheck /> 5 PPC Campaigns</li>
                        <li><FiCheck /> Digital Marketing</li>
                        <li><FiCheck /> Marketing Agency</li>
                        <li><FiCheck /> Seo Friendly</li>
                        <li><FiCheck /> UI/UX designs</li>
                      </ul>
                    </div>
                    <div className="pricing-footer">
                      <a className="rn-btn" href="#pricing">Purchase Now</a>
                    </div>
                  </div>
                </div>
              </div>
              <div className="col-lg-4 col-md-6 col-12">
                <div className="rn-pricing">
                  <div className="pricing-table-inner">
                    <div className="pricing-header">
                      <h4 className="title">Advanced</h4>
                      <div className="pricing">
                        <span className="price">29</span>
                        <span className="subtitle">USD Per Month</span>
                      </div>
                    </div>
                    <div className="pricing-body">
                      <ul className="list-style--1">
                        <li><FiCheck /> 5 PPC Campaigns</li>
                        <li><FiCheck /> Digital Marketing</li>
                        <li><FiCheck /> Marketing Agency</li>
                        <li><FiCheck /> Seo Friendly</li>
                        <li><FiCheck /> UI/UX designs</li>
                      </ul>
                    </div>
                    <div className="pricing-footer">
                      <a className="rn-btn" href="#pricing">Purchase Now</a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default PricingTable;
```

---

### 11. Testimonial.jsx

**Purpose**: Displays user testimonials with two different testimonial styles (`TestimonialOne` and `TestimonialTwo`).

**Key Features**:
- **Helmet** and **Breadcrumb** for page metadata and navigation.
- Showcases testimonials in an engaging manner.
- Includes a back-to-top button.

```jsx
import React from 'react';
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";
import TestimonialOne from "./testimonial/TestimonialOne";
import TestimonialTwo from "./testimonial/TestimonialTwo";

const Testimonial = () => {
  return (
    <>
      <PageHelmet pageTitle='Testimonial' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Testimonial'} />
      <main className="page-wrapper">
        <div className="rn-testimonial-area bg_color--1 ptb--120">
          <div className="container">
            <TestimonialOne />
          </div>
        </div>
        <div className="rn-testimonial-area">
          <div className="container">
            <TestimonialTwo />
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Testimonial;
```

---

### 12. Team.jsx

**Purpose**: Displays team members using two different team styles (`TeamOne` and `TeamTwo`), highlighting skills and social media links.

**Key Features**:
- **Helmet** and **Breadcrumb** for navigation and metadata.
- Showcases team members with names, designations, and social links.
- Includes a back-to-top button for ease of navigation.

```jsx
import React from 'react';
import TeamOne from "./team/TeamOne";
import TeamTwo from "./team/TeamTwo";
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";

const Team = () => {
  return (
    <>
      <PageHelmet pageTitle='Team' />
      <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
      <Breadcrumb title={'Team'} />
      <main className="page-wrapper">
        <div className="rn-team-wrapper ptb--120 bg_color--1">
          <div className="rn-team-area">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="section-title text-center mb--30">
                    <h2>Our Skilled Team</h2>
                    <p>There are many variations of passages of Lorem Ipsum available, <br /> but the majority have suffered alteration.</p>
                  </div>
                </div>
              </div>
              <TeamOne column="col-lg-4" teamStyle="" item="3" />
            </div>
          </div>
        </div>
        <div className="rn-team-wrapper ptb--120 bg_color--5">
          <div className="rn-team-area">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="section-title text-center mb--30">
                    <h2>Our Skilled Team</h2>
                    <p>There are many variations of passages of Lorem Ipsum available, <br /> but the majority have suffered alteration.</p>
                  </div>
                </div>
              </div>
              <TeamTwo column="col-lg-3" teamStyle="" item="4" />
            </div>
          </div>
        </div>
        <div className="rn-team-wrapper ptb--120 bg_color--1">
          <div className="rn-team-area">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="section-title text-center mb--30">
                    <h2>Our Skilled Team</h2>
                    <p>There are many variations of passages of Lorem Ipsum available, <br /> but the majority have suffered alteration.</p>
                  </div>
                </div>
              </div>
              <TeamOne column="col-lg-3" teamStyle="team-style--bottom" item="8" />
            </div>
          </div>
        </div>
      </main>
      <div className="backto-top">
        <ScrollToTop showUnder={160}>
          <FiChevronUp />
        </ScrollToTop>
      </div>
      <Footer />
    </>
  )
}

export default Team;
```

---

### 13. VideoPopup.jsx

**Purpose**: Displays videos in a popup modal, allowing users to view embedded YouTube videos.

**Key Features**:
- Uses `react-modal-video` for video playback in modals.
- Displays multiple video sections with different layouts.
- Includes a back-to-top button for user convenience.

```jsx
import React, { Component } from "react";
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
import ScrollToTop from 'react-scroll-up';
import { FiChevronUp } from "react-icons/fi";
import Header from "../component/header/Header";
import Footer from "../component/footer/Footer";
import ModalVideo from 'react-modal-video';

class VideoPopup extends Component {
  constructor() {
    super()
    this.state = { isOpen: false }
    this.openModal = this.openModal.bind(this)
  }

  openModal() {
    this.setState({ isOpen: true })
  }

  render() {
    return (
      <>
        <PageHelmet pageTitle='Video Popup' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Video Popup'} />
        <main className="page-wrapper">
          <div className="rn-section ptb--120 bg_color--1 line-separator">
            <div className="container">
              <div className="row sercice-details-content align-items-center">
                <div className="col-lg-12">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/blog/bl-big-01.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="rn-section ptb--120 bg_color--1 line-separator">
            <div className="container">
              <div className="row sercice-details-content align-items-center">
                <div className="col-lg-6">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/portfolio/portfolio-big-02.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center theme-color" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
                <div className="col-lg-6">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/portfolio/portfolio-big-03.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center black-color" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="rn-section ptb--120 bg_color--1">
            <div className="container">
              <div className="row sercice-details-content align-items-center">
                <div className="col-lg-4">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/portfolio/portfolio-big-02.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center theme-color md-size" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
                <div className="col-lg-4">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/portfolio/portfolio-big-01.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center theme-color md-size" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
                <div className="col-lg-4">
                  <div className="thumb position-relative">
                    <img className="w-100" src="/assets/images/portfolio/portfolio-big-03.jpg" alt="Service Images" />
                    <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
                    <button className="video-popup position-top-center theme-color md-size" onClick={this.openModal}><span className="play-icon"></span></button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </main>
        <div className="backto-top">
          <ScrollToTop showUnder={160}>
            <FiChevronUp />
          </ScrollToTop>
        </div>
        <Footer />
      </>
    )
  }
}

export default VideoPopup;
```

---

### 14. VideoModal.jsx

**Purpose**: This component is a simpler version of video display using a modal, allowing users to play a YouTube video.

**Key Features**:
- Utilizes `react-modal-video` for modal-based video playback.
- Simple and easy-to-integrate structure.

```jsx
import React, { Component } from 'react';
import ModalVideo from 'react-modal-video';

class VideoModal extends Component {
  constructor(props) {
    super(props)
    this.state = { isOpen: false }
  }

  openModal = () => {
    this.setState({ isOpen: true })
  }

  render() {
    return (
      <>
        <ModalVideo channel='youtube' isOpen={this.state.isOpen} videoId='ZOoVOfieAF8' onClose={() => this.setState({ isOpen: false })} />
        <button className="video-popup position-top-center" onClick={this.openModal}><span className="play-icon"></span></button>
      </>
    )
  }
}

export default VideoModal;
```

---

### 15. ProgressTwo.jsx

**Purpose**: Displays multiple progress bars with custom styling, showcasing different skill levels or progress statuses.

**Key Features**:
- Utilizes `react-bootstrap` for progress bar components.
- Customizable styling for each progress bar.

```jsx
import React from 'react';
import { ProgressBar } from 'react-bootstrap';

const ProgressTwo = (props) => {
  return (
    <div className={`rn-progress-bar ${props.ProgressStyle}`}>
      <div className="single-progress custom-color--1">
        <h6 className="title">Designing</h6>
        <ProgressBar now={81} />
        <span className="label">81%</span>
      </div>
      <div className="single-progress custom-color--2">
        <h6 className="title">Management</h6>
        <ProgressBar now={72} />
        <span className="label">72%</span>
      </div>
      <div className="single-progress custom-color--3">
        <h6 className="title">Marketing</h6>
        <ProgressBar now={89} />
        <span className="label">89%</span>
      </div>
      <div className="single-progress custom-color--4">
        <h6 className="title">Development</h6>
        <ProgressBar now={57} />
        <span className="label">57%</span>
      </div>
    </div>
  )
}

export default ProgressTwo;
```

---

### 16. ProgressOne.jsx

**Purpose**: Displays progress bars with default styling, showcasing progress in different areas like designing and development.

**Key Features**:
- Utilizes `react-bootstrap` for progress bar components.
- Default styling for each progress bar.

```jsx
import React from 'react';
import { ProgressBar } from 'react-bootstrap';

const ProgressOne = (props) => {
  return (
    <div className={`rn-progress-bar ${props.ProgressStyle}`}>
      <div className="single-progress">
        <h6 className="title">Designing</h6>
        <ProgressBar now={95} />
        <span className="label">95%</span>
      </div>
      <div className="single-progress">
        <h6 className="title">Management</h6>
        <ProgressBar now={85} />
        <span className="label">85%</span>
      </div>
      <div className="single-progress">
        <h6 className="title">Marketing</h6>
        <ProgressBar now={75} />
        <span className="label">75%</span>
      </div>
      <div className="single-progress">
        <h6 className="title">Development</h6>
        <ProgressBar now={80} />
        <span className="label">80%</span>
      </div>
    </div>
  )
}

export default ProgressOne;
```

---

### 17. TeamOne.jsx

**Purpose**: Displays team members using a specific style, providing images, titles, designations, and social media links.

**Key Features**:
- Integrates data from `data.jsx` for team member information.
- Displays team members with a specific style and layout.

```jsx
import React from 'react';
import data from "./data";

const TeamOne = (props) => {
  const itemSlice = data.slice(0, props.item)

  return (
    <div className="row">
      {itemSlice.map((value, i) => (
        <div className={`${props.column}`} key={i}>
          <div className={`team ${props.teamStyle}`}>
            <div className="thumbnail">
              <img src={`/assets/images/team/team-${value.images}.jpg`} alt="Blog Images" />
            </div>
            <div className="content">
              <h4 className="title">{value.title}</h4>
              <p className="designation">{value.designation}</p>
            </div>
            <ul className="social-icon">
              {value.socialNetwork.map((social, index) => <li key={index}><a href={`${social.url}`}>{social.icon}</a></li>)}
            </ul>
          </div>
        </div>
      ))}
    </div>
  )
}

export default TeamOne;
```

---

### 18. data.jsx

**Purpose**: Contains data for team members, including images, titles, designations, and social media links.

**Key Features**:
- Provides a list of team members with their respective information.
- Used by components like `TeamOne` and `TeamTwo` to populate team details.

```jsx
import React from "react";
import { FaFacebookF, FaLinkedinIn, FaTwitter } from "react-icons/fa";

let data = [
  {
    images: '01',
    title: 'Jone Due',
    designation: 'Sr. Web Developer',
    socialNetwork: [
      { icon: <FaFacebookF />, url: '#' },
      { icon: <FaLinkedinIn />, url: '#' },
      { icon: <FaTwitter />, url: '#' },
    ]
  },
  { ... },
  { ... },
];

export default data;
```

---

### 19. TeamTwo.jsx

**Purpose**: Displays team members using a different style, similar to `TeamOne`, but with a slightly varied layout.

**Key Features**:
- Integrates data from `data.jsx` for team member information.
- Displays team members with a different style and layout compared to `TeamOne`.

```jsx
import React from 'react';
import data from "./data";

const TeamTwo = (props) => {
  const itemSlice = data.slice(0, props.item)

  return (
    <div className="row">
      {itemSlice.map((value, i) => (
        <div className={`${props.column}`} key={i}>
          <div className={`team-static ${props.teamStyle}`}>
            <div className="thumbnail">
              <img src={`/assets/images/team/team-${value.images}.jpg`} alt="Blog Images" />
            </div>
            <div className="inner">
              <div className="content">
                <h4 className="title">{value.title}</h4>
                <p className="designation">{value.designation}</p>
              </div>
              <ul className="social-transparent liststyle d-flex">
                {value.socialNetwork.map((social, index) => <li key={index}><a href={`${social.url}`}>{social.icon}</a></li>)}
              </ul>
            </div>
          </div>
        </div>
      ))}
    </div>
  )
}

export default TeamTwo;
```

---

### 20. TestimonialTwo.jsx

**Purpose**: Currently a placeholder component, likely designed for future testimonial content or integration.

**Key Features**:
- Basic structure with no content.
- Serves as a placeholder for potential future use.

```jsx
import React from 'react';

const TestimonialTwo = () => {
  return (
    <div>
    </div>
  )
}

export default TestimonialTwo;
```

---

### 21. TestimonialOne.jsx

**Purpose**: Displays testimonials using a tab-based interface, showcasing user feedback in a structured manner.

**Key Features**:
- Utilizes `react-tabs` for tabbed testimonial display.
- Displays author information alongside each testimonial.

```jsx
import React from 'react';
import { Tab, Tabs, TabList, TabPanel } from 'react-tabs';

const TestimonialOne = () => {
  return (
    <div className="row">
      <div className="col-lg-12">
        <Tabs>
          <TabPanel>
            <div className="rn-testimonial-content text-center">
              <div className="inner">
                <p>Aklima The standard chunk of Lorem Ipsum...</p>
              </div>
              <div className="author-info">
                <h6><span>Aklima </span> - COO, AMERIMAR ENTERPRISES, INC.</h6>
              </div>
            </div>
          </TabPanel>
          { /* Other TabPanels */ }
          <TabList className="testimonial-thumb-wrapper">
            <Tab>
              <div className="testimonial-thumbnai">
                <div className="thumb">
                  <img src="/assets/images/client/testimonial-1.jpg" alt="Testimonial Images" />
                </div>
              </div>
            </Tab>
            { /* Other Tabs */ }
          </TabList>
        </Tabs>
      </div>
    </div>
  )
}

export default TestimonialOne;
```

---

This documentation should help you understand the structure and usage of each component in your application. If you have any questions or need further assistance, feel free to reach out. Happy coding! 🎉