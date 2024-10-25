# Documentation for React Components

Welcome to the comprehensive documentation for the React components included in this project. Below, you will find detailed descriptions of each component, its purpose, and how it can be used effectively in your applications. Each section includes code snippets, tables, and lists to facilitate understanding. 📝✨

## Index

1. [Accordion Component](#accordion-component)
2. [About Component](#about-component)
3. [Blog Components](#blog-components)
   - BlogDetails
   - Blog
   - BlogList
   - BlogContent
4. [Brand Components](#brand-components)
   - BrandTwo
   - Brand
5. [Contact Components](#contact-components)
   - Contact
   - ContactOne
   - ContactTwo
   - ContactThree
6. [Error Component](#error-component)
7. [Portfolio Components](#portfolio-components)
   - PortfolioDetails
   - Portfolio
   - PortfolioGalleryPopup
   - PortfolioList
   - PortfolioMasonry
   - PortfolioOne
   - PortfolioTwo
8. [Service Components](#service-components)
   - ServiceDetails
   - Service
   - ServiceOne
   - ServiceList
   - ServiceTwo
9. [Team Components](#team-components)
   - Team
   - TeamOne
10. [Testimonial Component](#testimonial-component)
11. [CallAction Component](#callaction-component)
12. [Pagination Component](#pagination-component)
13. [Breadcrumb Component](#breadcrumb-component)
14. [SectionTitle Component](#sectiontitle-component)
15. [Tab Components](#tab-components)
    - TabOne
    - TabTwo
    - TabThree

---

### Accordion Component

**Filename:** `Accordion.jsx`

**Purpose:**  
The `Accordion` component is used to display collapsible content panels for presenting information in a limited space.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Accordion, AccordionItem, AccordionItemHeading, AccordionItemPanel, AccordionItemButton } from 'react-accessible-accordion';
import 'react-accessible-accordion/dist/fancy-example.css';

class Accordion01 extends Component {
  render() {
    return (
      <Accordion className="accodion-style--1" preExpanded={'0'}>
        <AccordionItem>
          <AccordionItemHeading>
            <AccordionItemButton>Your Business Skills But Never Stop Improving.</AccordionItemButton>
          </AccordionItemHeading>
          <AccordionItemPanel>
            <p>Lorem ipsum dolor sit amet...</p>
          </AccordionItemPanel>
        </AccordionItem>
        {/* Additional Accordion Items */}
      </Accordion>
    );
  }
}

export default Accordion01;
```

### About Component

**Filename:** `About.jsx`

**Purpose:**  
The `About` component is designed to provide information about the website or company, including team members, testimonials, and brand partners.

**Key Features:**
- Displays an "About Us" section with descriptive text and images.
- Integrates a team display and testimonials.
- Includes a "Fun Facts" counter and a call to action section.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import PageHelmet from "../component/common/Helmet";
import Breadcrumb from "../elements/common/Breadcrumb";
// Additional imports

class About extends Component {
  render() {
    let title = 'About', description = 'There are many variations of passages of Lorem Ipsum available...';
    return (
      <React.Fragment>
        <PageHelmet pageTitle='About' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'About'} />
        {/* About Section */}
        <div className="rn-about-area ptb--120 bg_color--1">
          <div className="rn-about-wrapper">
            {/* Content here */}
          </div>
        </div>
        <Footer />
      </React.Fragment>
    );
  }
}

export default About;
```

### Blog Components

#### BlogDetails Component

**Filename:** `BlogDetails.jsx`

**Purpose:**  
Displays the details of a specific blog post, including the content, comments, and a video modal.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import PageHelmet from "../component/common/Helmet";
// Additional imports

class BlogDetails extends Component {
  constructor () {
    super();
    this.state = { isOpen: false };
    this.openModal = this.openModal.bind(this);
  }

  openModal () {
    this.setState({isOpen: true});
  }

  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Blog Details' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        {/* Blog Details Content */}
        <Footer />
      </React.Fragment>
    );
  }
}

export default BlogDetails;
```

#### Blog Component

**Filename:** `Blog.jsx`

**Purpose:**  
Serves as an overview page listing all blogs with pagination.

**Code Snippet:**
```jsx
import React, { Component } from "react";
// Additional imports

class Blog extends Component {
  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Blog' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Blog List'} />
        <div className="rn-blog-area ptb--120 bg_color--1">
          <div className="container">
            <BlogList />
            <Pagination />
          </div>
        </div>
        <Footer />
      </React.Fragment>
    );
  }
}

export default Blog;
```

#### BlogList Component

**Filename:** `BlogList.jsx`

**Purpose:**  
Renders a list of blog posts with a thumbnail, title, and category.

**Code Snippet:**
```jsx
import React, { Component, Fragment } from "react";
import BlogContent from "./BlogContent";

class BlogList extends Component {
  render() {
    const PostList = BlogContent.slice(0, 6);
    return (
      <Fragment>
        <div className="row">
          {PostList.map((value, i) => (
            <div className="col-lg-4 col-md-6 col-sm-6 col-12" key={i}>
              <div className="blog blog-style--1">
                <div className="thumbnail">
                  <a href="/blog-details">
                    <img className="w-100" src={`/assets/images/blog/blog-${value.images}.jpg`} alt="Blog Images" />
                  </a>
                </div>
                <div className="content">
                  <p className="blogtype">{value.category}</p>
                  <h4 className="title"><a href="/blog-details">{value.title}</a></h4>
                  <a className="rn-btn text-white" href="/blog-details">Read More</a>
                </div>
              </div>
            </div>
          ))}
        </div>
      </Fragment>
    );
  }
}

export default BlogList;
```

#### BlogContent Component

**Filename:** `BlogContent.jsx`

**Purpose:**  
Provides static data for the blog posts used in `BlogList`.

**Code Snippet:**
```jsx
const BlogContent = [
  {
    images: '01',
    title: 'Getting tickets to the big show',
    category: 'Development'
  },
  // Additional blog entries
];

export default BlogContent;
```

### Brand Components

#### BrandTwo Component

**Filename:** `BrandTwo.jsx`

**Purpose:**  
Displays a list of brand logos in a grid format.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class BrandTwo extends Component {
  render() {
    return (
      <React.Fragment>
        <ul className="brand-style-2">
          <li><img src="/assets/images/brand/brand-01.png" alt="Logo Images" /></li>
          {/* Additional brand logos */}
        </ul>
      </React.Fragment>
    );
  }
}

export default BrandTwo;
```

#### Brand Component

**Filename:** `Brand.jsx`

**Purpose:**  
Similar to `BrandTwo`, but with customizable styles through props.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class Brand extends Component {
  render() {
    const { branstyle } = this.props;
    return (
      <React.Fragment>
        <ul className={`brand-list ${branstyle}`}>
          <li><img src="/assets/images/brand/brand-01.png" alt="Logo Images" /></li>
          {/* Additional brand logos */}
        </ul>
      </React.Fragment>
    );
  }
}

export default Brand;
```

### Contact Components

#### Contact Component

**Filename:** `Contact.jsx`

**Purpose:**  
Provides a contact page with contact information, a map, and a contact form.

**Code Snippet:**
```jsx
import React, { Component } from "react";
// Additional imports

class Contact extends Component {
  static defaultProps = {
    center: { lat: 59.95, lng: 30.33 },
    zoom: 11
  };

  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Contact' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        {/* Contact Information and Map */}
        <Footer />
      </React.Fragment>
    );
  }
}

export default Contact;
```

#### ContactOne Component

**Filename:** `ContactOne.jsx`

**Purpose:**  
Offers a simple contact form with fields for name, email, subject, and message.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class ContactOne extends Component {
  constructor(props) {
    super(props);
    this.state = {
      rnName: '',
      rnEmail: '',
      rnSubject: '',
      rnMessage: '',
    };
  }

  render() {
    return (
      <div className="contact-form--1">
        <div className="container">
          <div className="row row--35 align-items-start">
            <div className="col-lg-6 order-2 order-lg-1">
              <div className="section-title text-left mb--50">
                <h2 className="title">Hire Me.</h2>
                <p className="description">I am available for freelance work...</p>
              </div>
              <form>
                {/* Form Fields */}
                <button className="rn-button-style--2 btn-solid" type="submit">Submit</button>
              </form>
            </div>
            <div className="col-lg-6 order-1 order-lg-2">
              <img src="/assets/images/about/about-6.jpg" alt="trydo" />
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default ContactOne;
```

#### ContactTwo Component

**Filename:** `ContactTwo.jsx`

**Purpose:**  
Similar to `ContactOne` but with different content and styling.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class ContactTwo extends Component {
  constructor(props) {
    super(props);
    this.state = {
      rnName: '',
      rnEmail: '',
      rnSubject: '',
      rnMessage: '',
    };
  }

  render() {
    return (
      <div className="contact-form--1">
        <div className="container">
          <div className="row row--35 align-items-start">
            <div className="col-lg-6 order-2 order-lg-1">
              <div className="section-title text-left mb--50">
                <h2 className="title">Contact Us.</h2>
                <p className="description">Lorem ipsum dolor sit amet...</p>
              </div>
              <form>
                {/* Form Fields */}
                <button className="rn-button-style--2 btn-solid" type="submit">Submit</button>
              </form>
            </div>
            <div className="col-lg-6 order-1 order-lg-2">
              <img src="/assets/images/about/about-6.jpg" alt="trydo" />
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default ContactTwo;
```

#### ContactThree Component

**Filename:** `ContactThree.jsx`

**Purpose:**  
Combines a contact form with a portfolio showcase.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import PortfolioList from "../../elements/portfolio/PortfolioList.jsx";

class ContactThree extends Component {
  constructor(props) {
    super(props);
    this.state = {
      rnName: "",
      rnEmail: "",
      rnSubject: "",
      rnMessage: "",
    };
  }

  render() {
    const { column, styevariation } = this.props;
    const list = PortfolioListContent.slice(0, this.props.item);

    return (
      <div className="contact-form--1">
        <div className="container">
          <div className="row row--35 align-items-start">
            <div className="col-lg-6 image-class">
              <div className="thumbnail mb_md--30 mb_sm--30">
                <img src={`${this.props.contactImages}`} alt="trydo" />
                <PortfolioList items={PortfolioListContent} />
              </div>
            </div>
            <div className="col-lg-6 form-class">
              <div className="section-title text-left mb--50">
                <h2 className="title sign-in-title">{this.props.contactTitle}</h2>
                <p className="description continue">Please sign in to continue</p>
              </div>
              <form>
                {/* Form Fields */}
                <button className="rn-button-style--2 btn-solid" type="submit">Sign in</button>
              </form>
              <div className="sign-in-bottom-content">
                <h3>- Or -</h3>
                <h4>Sign in with</h4>
                <h6>Not a Member yet?<span className="sign-up"> Sign Up</span></h6>
                <p>By signing up you are agreeing to our <span>terms & conditions</span> and <span>privacy policy</span>.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default ContactThree;
```

### Error Component

**Filename:** `error404.jsx`

**Purpose:**  
Displays a 404 error page when a user navigates to a non-existent route.

**Code Snippet:**
```jsx
import React, { Component } from 'react';
import Header from "../component/header/HeaderFour";
import Footer from "../component/footer/FooterTwo";

class error404 extends Component {
  render() {
    return (
      <>
        <Header headerPosition="header--transparent" color="color-white" logo="logo-light" />
        <div className="error-page-inner bg_color--4">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="inner">
                  <h1 className="title theme-gradient">404!</h1>
                  <h3 className="sub-title">Page not found</h3>
                  <span>The page you were looking for could not be found.</span>
                  <a className="rn-button-style--2 btn-solid" href="/">Back To Homepage</a>
                </div>
              </div>
            </div>
          </div>
        </div>
        <Footer />
      </>
    );
  }
}

export default error404;
```

### Portfolio Components

#### PortfolioDetails Component

**Filename:** `PortfolioDetails.jsx`

**Purpose:**  
Displays detailed information about a specific portfolio item, including a video and related works.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import ModalVideo from 'react-modal-video';
// Additional imports

class PortfolioDetails extends Component {
  constructor () {
    super();
    this.state = { isOpen: false };
    this.openModal = this.openModal.bind(this);
  }

  openModal () {
    this.setState({isOpen: true});
  }

  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Portfolio Details' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        {/* Portfolio Details Content */}
        <Footer />
      </React.Fragment>
    );
  }
}

export default PortfolioDetails;
```

#### Portfolio Component

**Filename:** `Portfolio.jsx`

**Purpose:**  
Serves as an overview page listing all portfolio items with a slick carousel for featured works.

**Code Snippet:**
```jsx
import React, { Component } from "react";
// Additional imports

class Portfolio extends Component {
  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Portfolio' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Portfolio'} />
        <div className="portfolio-area pt--120 pb--140 bg_color--5">
          {/* Slick Carousel for Featured Works */}
        </div>
        <div className="portfolio-area ptb--120 bg_color--1">
          {/* All Works */}
        </div>
        <Footer />
      </React.Fragment>
    );
  }
}

export default Portfolio;
```

#### PortfolioGalleryPopup Component

**Filename:** `PortfolioGalleryPopup.jsx`

**Purpose:**  
Displays a gallery of portfolio items with lightbox functionality for viewing larger images.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import Lightbox from 'react-image-lightbox';

class PortfolioGalleryPopup extends Component {
  constructor(props) {
    super(props);
    this.state = {
      photoIndex: 0,
      isOpen: false,
    };
  }

  render() {
    const { column, item } = this.props;
    const list = PortfolioList.slice(0, item);
    const { photoIndex, isOpen } = this.state;

    return (
      <React.Fragment>
        {isOpen && (
          <Lightbox mainSrc={images[photoIndex]} nextSrc={images[(photoIndex + 1) % images.length]} prevSrc={images[(photoIndex + images.length - 1) % images.length]} onCloseRequest={() => this.setState({ isOpen: false })} onMovePrevRequest={() => this.setState({ photoIndex: (photoIndex + images.length - 1) % images.length })} onMoveNextRequest={() => this.setState({ photoIndex: (photoIndex + 1) % images.length })} />
        )}
        {list.map((value, index) => (
          <div className={`${column}`} key={index}>
            <div className="portfolio-tilthover">
              <div onClick={() => this.setState({ isOpen: true, photoIndex: index })} className="Tilt-inner">
                <div className="portfolio">
                  <div className="thumbnail-inner">
                    <div className={`thumbnail ${value.image}`}></div>
                    <div className={`bg-blr-image ${value.image}`}></div>
                  </div>
                  <div className="content">
                    <div className="inner">
                      <p>{value.category}</p>
                      <h4><a href="#portfolio-details">{value.title}</a></h4>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default PortfolioGalleryPopup;
```

#### PortfolioList Component

**Filename:** `PortfolioList.jsx`

**Purpose:**  
Renders a list of portfolio items for display in grid layout.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Link } from "react-router-dom";

class PortfolioList extends Component {
  render() {
    const { column, styevariation } = this.props;
    const list = PortfolioListContent.slice(0, this.props.item);

    return (
      <React.Fragment>
        {list.map((value, index) => (
          <div className={`${column}`} key={index}>
            <div className={`portfolio ${styevariation}`}>
              <div className="thumbnail-inner">
                <div className={`thumbnail ${value.image}`}></div>
                <div className={`bg-blr-image ${value.image}`}></div>
              </div>
              <div className="content">
                <div className="inner">
                  <p>{value.category}</p>
                  <h4><a href="/portfolio-details">{value.title}</a></h4>
                  <a className="rn-btn" href="/portfolio-details">View Details</a>
                </div>
              </div>
              <Link className="link-overlay" to="/portfolio-details"></Link>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default PortfolioList;
```

#### PortfolioMasonry Component

**Filename:** `PortfolioMasonry.jsx`

**Purpose:**  
Displays a masonry layout of portfolio items.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Link } from "react-router-dom";

class PortfolioMasonry extends Component {
  render() {
    const { column } = this.props;
    const list = PortfolioList.slice(0, this.props.item);

    return (
      <React.Fragment>
        {list.map((value, index) => (
          <div className={`${column}`} key={index}>
            <div className="Tilt-inner">
              <div className="portfolio">
                <div className="thumbnail-inner">
                  <div className={`thumbnail ${value.image}`}></div>
                  <div className={`bg-blr-image ${value.image}`}></div>
                </div>
                <div className="content">
                  <div className="inner">
                    <p>{value.category}</p>
                    <h4><a href="/portfolio-details">{value.title}</a></h4>
                    <a className="rn-btn" href="/portfolio-details">Case Study</a>
                  </div>
                </div>
                <Link className="link-overlay" to="/portfolio-details"></Link>
              </div>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default PortfolioMasonry;
```

#### PortfolioOne Component

**Filename:** `PortfolioOne.jsx`

**Purpose:**  
Provides a simple column layout for portfolio items.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class PortfolioOne extends Component {
  render() {
    return (
      <React.Fragment>
        {PortfolioList.map((value, index) => (
          <div className="col-lg-3" key={index}>
            <div className="portfolio">
              <div className="thumbnail-inner">
                <div className={`thumbnail ${value.image}`}></div>
                <div className={`bg-blr-image ${value.image}`}></div>
              </div>
              <div className="content">
                <div className="inner">
                  <p>{value.category}</p>
                  <h4><a href="/portfolio-details">{value.title}</a></h4>
                  <a className="rn-btn" href="/portfolio-details">Case Study</a>
                </div>
              </div>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default PortfolioOne;
```

#### PortfolioTwo Component

**Filename:** `PortfolioTwo.jsx`

**Purpose:**  
Displays portfolio items in a carousel format using the `react-slick` library.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import Slider from "react-slick";

class PortfolioTwo extends Component {
  render() {
    return (
      <React.Fragment>
        <div className="portfolio-sacousel-inner mt--60">
          <Slider {...portfolioSlick}>
            {PortfolioList.map((value, index) => (
              <div className="portfolio portfolio-style--2" key={index}>
                <div className="inner">
                  <div className="thumbnail-inner">
                    <div className={`thumbnail ${value.image}`}></div>
                    <div className={`bg-blr-image ${value.image}`}></div>
                  </div>
                  <div className="content">
                    <div className="inner">
                      <p>{value.category}</p>
                      <h4><a href="/portfolio-details">{value.title}</a></h4>
                      <a className="rn-btn" href="/portfolio-details">Case Study</a>
                    </div>
                  </div>
                </div>
              </div>
            ))}
          </Slider>
        </div>
      </React.Fragment>
    );
  }
}

export default PortfolioTwo;
```

### Service Components

#### ServiceDetails Component

**Filename:** `ServiceDetails.jsx`

**Purpose:**  
Provides detailed information about a specific service, including images and process descriptions.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import ModalVideo from 'react-modal-video';

class ServiceDetails extends Component {
  constructor () {
    super();
    this.state = { isOpen: false };
    this.openModal = this.openModal.bind(this);
  }

  openModal () {
    this.setState({isOpen: true});
  }

  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Service Details' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        {/* Service Details Content */}
        <Footer />
      </React.Fragment>
    );
  }
}

export default ServiceDetails;
```

#### Service Component

**Filename:** `Service.jsx`

**Purpose:**  
Lists all services offered, categorized into sections like Digital Marketing, Strategy, Creative Agency, and Development.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class Service extends Component {
  render() {
    return (
      <React.Fragment>
        <PageHelmet pageTitle='Service' />
        <Header headertransparent="header--transparent" colorblack="color--black" logoname="logo.png" />
        <Breadcrumb title={'Service'} />
        <div className="service-area ptb--120 bg_color--5">
          <div className="container">
            {/* Service Sections */}
          </div>
        </div>
        <Footer />
      </React.Fragment>
    );
  }
}

export default Service;
```

#### ServiceOne Component

**Filename:** `ServiceOne.jsx`

**Purpose:**  
Renders a simple list of services with icons.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class ServiceOne extends Component {
  render() {
    return (
      <React.Fragment>
        <div className="row">
          {ServiceList.map((val, i) => (
            <div className="col-lg-4 col-md-6 col-sm-6 col-12" key={i}>
              <div className="service service__style--1">
                <div className="icon">
                  <img src={`/assets/images/icons/icon-${val.icon}.png`} alt="Digital Agency" />
                </div>
                <div className="content">
                  <h4 className="title">{val.title}</h4>
                  <p>{val.description}</p>
                </div>
              </div>
            </div>
          ))}
        </div>
      </React.Fragment>
    );
  }
}

export default ServiceOne;
```

#### ServiceList Component

**Filename:** `ServiceList.jsx`

**Purpose:**  
Displays a list of services with icons and descriptions, with support for custom images.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class ServiceThree extends Component {
  render() {
    const { column } = this.props;
    const ServiceContent = ServiceList.slice(0, this.props.item);

    return (
      <React.Fragment>
        <div className="row">
          {ServiceContent.map((val, i) => (
            <div className={`${column}`} key={i}>
              <a href="/service-details">
                <div className="service service__style--2">
                  <div className="icon">{val.icon}</div>
                  <div className="content">
                    <h3 className="title">{val.title}</h3>
                    <p>{val.description}</p>
                  </div>
                  <div className="image">
                    <p>{val.photo}</p>
                  </div>
                </div>
              </a>
            </div>
          ))}
        </div>
      </React.Fragment>
    );
  }
}

export default ServiceThree;
```

#### ServiceTwo Component

**Filename:** `ServiceTwo.jsx`

**Purpose:**  
Renders a detailed list of services with descriptions and call-to-action buttons.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class ServiceTwo extends Component {
  render() {
    let title = 'Services', description = 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration.';

    return (
      <React.Fragment>
        <div className="row">
          <div className="col-lg-4 col-12">
            <div className="section-title mt--30 mt_md--5 mt_mobile--5 mb_mobile--10">
              <h2 className="title">{title}</h2>
              <p>{description}</p>
              <a className="btn-transparent rn-btn-dark" href="/service"><span className="text">Request Custom Service</span></a>
            </div>
          </div>
          <div className="col-lg-8 col-12 mt_md--50">
            <div className="row service-one-wrapper">
              {ServiceList.map((val, i) => (
                <div className="col-lg-6 col-md-6 col-sm-6 col-12" key={i}>
                  <a href="/service-details">
                    <div className="service service__style--2">
                      <div className="icon">{val.icon}</div>
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
      </React.Fragment>
    );
  }
}

export default ServiceTwo;
```

### Team Components

#### Team Component

**Filename:** `Team.jsx`

**Purpose:**  
Displays a list of team members with their details and social media links.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class Team extends Component {
  render() {
    const { column } = this.props;

    return (
      <React.Fragment>
        {TeamContent.map((value, i) => (
          <div className={`${column}`} key={i}>
            <div className="team">
              <div className="thumbnail">
                <img src={`/assets/images/team/team-${value.images}.jpg`} alt="Blog Images" />
              </div>
              <div className="content">
                <h4 className="title">{value.title}</h4>
                <p className="designation">{value.designation}</p>
              </div>
              <ul className="social-icon">
                {value.socialNetwork.map((social, index) => (
                  <li key={index}><a href={`${social.url}`}>{social.icon}</a></li>
                ))}
              </ul>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default Team;
```

#### TeamOne Component

**Filename:** `TeamOne.jsx`

**Purpose:**  
Variant of the `Team` component, providing similar functionality with a distinct layout.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class TeamOne extends Component {
  render() {
    const { column } = this.props;

    return (
      <React.Fragment>
        {TeamContent.map((value, i) => (
          <div className={`${column}`} key={i}>
            <div className="team">
              <div className="thumbnail">
                <img src={`/assets/images/team/team-${value.images}.jpg`} alt="Blog Images" />
              </div>
              <div className="content">
                <h4 className="title">{value.title}</h4>
                <p className="designation">{value.designation}</p>
              </div>
              <ul className="social-icon">
                {value.socialNetwork.map((social, index) => (
                  <li key={index}><a href={`${social.url}`}>{social.icon}</a></li>
                ))}
              </ul>
            </div>
          </div>
        ))}
      </React.Fragment>
    );
  }
}

export default TeamOne;
```

### Testimonial Component

**Filename:** `Testimonial.jsx`

**Purpose:**  
Displays a carousel of testimonials with author information.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Tab, Tabs, TabList, TabPanel } from 'react-tabs';

class Testimonial extends Component {
  render() {
    return (
      <React.Fragment>
        <div className="row">
          <div className="col-lg-12">
            <Tabs>
              <TabPanel>
                <div className="rn-testimonial-content text-center">
                  <div className="inner">
                    <p>Aklima The standard chunk of Lorem Ipsum used...</p>
                  </div>
                  <div className="author-info">
                    <h6><span>Aklima </span> - COO, AMERIMAR ENTERPRISES, INC.</h6>
                  </div>
                </div>
              </TabPanel>
              {/* Additional Tab Panels */}
              <TabList className="testimonial-thumb-wrapper">
                <Tab>
                  <div className="testimonial-thumbnai">
                    <div className="thumb">
                      <img src="/assets/images/client/testimonial-1.jpg" alt="Testimonial Images" />
                    </div>
                  </div>
                </Tab>
                {/* Additional Tabs */}
              </TabList>
            </Tabs>
          </div>
        </div>
      </React.Fragment>
    );
  }
}

export default Testimonial;
```

### CallAction Component

**Filename:** `CallAction.jsx`

**Purpose:**  
Provides a call-to-action section encouraging users to contact the business.

**Code Snippet:**
```jsx
import React from 'react';

const CallAction = () => {
  return (
    <div className="call-to-action-wrapper call-to-action text-white-wrapper ptb--120">
      <div className="container">
        <div className="row">
          <div className="col-lg-12">
            <div className="inner text-center">
              <span>READY TO DO THIS</span>
              <h2>Let's get to work</h2>
              <a className="rn-button-style--2" href="/contact"><span>Contact Us</span></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}

export default CallAction;
```

### Pagination Component

**Filename:** `Pagination.jsx`

**Purpose:**  
Provides pagination controls for navigating through pages of content.

**Code Snippet:**
```jsx
import React from 'react';
import { Link } from 'react-router-dom';
import { FaAngleRight } from "react-icons/fa";

export default function Pagination() {
  return (
    <div className="rn-pagination text-center">
      <ul className="page-list">
        <li className="active"><Link to="#">1</Link></li>
        <li><Link to="#">2</Link></li>
        <li><Link to="#">3</Link></li>
        <li><Link to="#">4</Link></li>
        <li><Link to="#"><FaAngleRight /></Link></li>
      </ul>
    </div>
  );
}
```

### Breadcrumb Component

**Filename:** `Breadcrumb.jsx`

**Purpose:**  
Displays a navigation breadcrumb for easy navigation back to previous sections.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Link } from "react-router-dom";

class Breadcrumb extends Component {
  render() {
    const { title, parent } = this.props;

    return (
      <React.Fragment>
        <div className="breadcrumb-area rn-bg-color ptb--120 bg_image bg_image--1" data-black-overlay="6">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <div className="breadcrumb-inner pt--100">
                  <h2 className="title">{title}</h2>
                  <ul className="page-list">
                    <li className="breadcrumb-item"><Link to={`${process.env.PUBLIC_URL}`}>Home</Link></li>
                    {parent ? <li className="breadcrumb-item">{parent}</li> : ''}
                    <li className="breadcrumb-item active">{title}</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </React.Fragment>
    );
  }
}

export default Breadcrumb;
```

### SectionTitle Component

**Filename:** `SectionTitle.jsx`

**Purpose:**  
Renders a section title with customizable color and text.

**Code Snippet:**
```jsx
import React, { Component, Fragment } from "react";

class SectionTitle extends Component {
  render() {
    const { title, textColor } = this.props;

    return (
      <Fragment>
        <div className="section-title-default">
          <h2 className={`title ${textColor}`}>{title}</h2>
        </div>
      </Fragment>
    );
  }
}

export default SectionTitle;
```

### Tab Components

#### TabOne Component

**Filename:** `TabOne.jsx`

**Purpose:**  
Displays a tabbed interface with sections such as history, mission, and support.

**Code Snippet:**
```jsx
import React, { Component } from "react";
import { Tab, Tabs, TabList, TabPanel } from 'react-tabs';

class TabsOne extends Component {
  render() {
    let tab1 = "Our history", tab2 = "Our mission", tab3 = "Friendly Support";
    const { tabStyle } = this.props;

    return (
      <div>
        <div className="tabs-area">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <Tabs>
                  <TabList className={`${tabStyle}`}>
                    <Tab>{tab1}</Tab>
                    <Tab>{tab2}</Tab>
                    <Tab>{tab3}</Tab>
                  </TabList>
                  <TabPanel>
                    <div className="single-tab-content">
                      <p>Lorem ipsum dolor sit amet...</p>
                      <ul className="list-style--1">
                        {namesItemOne.map((name, index) => (
                          <li key={index}><FiCheck /> {name}</li>
                        ))}
                      </ul>
                    </div>
                  </TabPanel>
                  {/* Additional Tab Panels */}
                </Tabs>
              </div>
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default TabsOne;
```

#### TabTwo Component

**Filename:** `TabTwo.jsx`

**Purpose:**  
Offers a tabbed interface with sections for main skills, awards, experience, and education.

**Code Snippet:**
```jsx
import React, { Component } from "react";

class TabsTwo extends Component {
  render() {
    let tab1 = "Main skills", tab2 = "Awards", tab3 = "Experience", tab4 = "Education & Certification";
    const { tabStyle } = this.props;

    return (
      <div>
        <div className="tabs-area">
          <div className="container">
            <div className="row">
              <div className="col-lg-12">
                <Tabs>
                  <TabList className={`${tabStyle}`}>
                    <Tab>{tab1}</Tab>
                    <Tab>{tab2}</Tab>
                    <Tab>{tab3}</Tab>
                    <Tab>{tab4}</Tab>
                  </TabList>
                  <TabPanel>
                    <div className="single-tab-content">
                      <ul>
                        <li><a href="/service">User experience design <span>- UI/UX</span></a> Delight the user and make it work.</li>
                        <li><a href="/service">Web and user interface design<span> - Development</span></a> Websites, web experiences...</li>
                        <li><a href="/service">Interaction design <span>- Animation</span></a> I like to move it move it.</li>
                      </ul>
                    </div>
                  </TabPanel>
                  {/* Additional Tab Panels */}
                </Tabs>
              </div>
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default TabsTwo;
```

#### TabThree Component

**Filename:** `TabThree.jsx`

**Purpose:**  
Shows a tabbed display with a lightbox feature for images in each category.

**Code Snippet:**
```jsx
import React, { Component } from 'react';
import { Tab, Tabs, TabList, TabPanel } from 'react-tabs';
import Lightbox from 'react-image-lightbox';

class TabStyleThree extends Component {
  constructor(props) {
    super(props);
    this.state = {
      tab1: 0,
      tab2: 0,
      tab3: 0,
      tab4: 0,
      isOpen: false,
    };
  }

  render() {
    const { column } = this.props;
    const { tab1, tab2, tab3, tab4, isOpen } = this.state;

    return (
      <div>
        <Tabs>
          <div className="row text-center">
            <div className="col-lg-12">
              <div className="tablist-inner">
                <TabList className="pv-tab-button text-center mt--0">
                  <Tab><span>All Project</span></Tab>
                  <Tab><span>Web Design</span></Tab>
                  <Tab><span>Logo Design</span></Tab>
                  <Tab><span>Mobile App</span></Tab>
                </TabList>
              </div>
            </div>
          </div>
          <TabPanel className="row row--35">
            {TabOne.map((value, index) => (
              <div className={`${column}`} key={index}>
                {isOpen && (
                  <Lightbox mainSrc={TabOne[tab1].bigImage} nextSrc={TabOne[(tab1 + 1) % TabOne.length]} prevSrc={TabOne[(tab1 + TabOne.length - 1) % TabOne.length]} onCloseRequest={() => this.setState({ isOpen: false })} onMovePrevRequest={() => this.setState({ tab1: (tab1 + TabOne.length - 1) % TabOne.length })} onMoveNextRequest={() => this.setState({ tab1: (tab1 + 1) % TabOne.length })} imageLoadErrorMessage='Image Loading ...' enableZoom={false} />
                )}
                <div className="item-portfolio-static">
                  <div onClick={() => this.setState({ isOpen: true, tab1: index })}>
                    <div className="portfolio-static">
                      <div className="thumbnail-inner">
                        <div className="thumbnail">
                          <a href="#portfolio-details">
                            <img src={`/assets/images/portfolio/dp-portfolio-${value.image}.jpg`} alt="Portfolio Images" />
                          </a>
                        </div>
                      </div>
                      <div className="content">
                        <div className="inner">
                          <p>{value.category}</p>
                          <h4><a href="#portfolio-details">{value.title}</a></h4>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            ))}
          </TabPanel>
          {/* Additional Tab Panels */}
        </Tabs>
      </div>
    );
  }
}

export default TabStyleThree;
```

This documentation provides an overview of each component, highlighting its purpose and key features, with code snippets to demonstrate its usage. Feel free to explore each component in detail to understand how they can be used and customized in your projects.