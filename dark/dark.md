# 📄 React Component Documentation

Welcome to the documentation for the **MainDemo.jsx** and **PortfolioLanding.jsx** files. These files are part of a React application, designed to create beautiful, responsive web pages with various features such as sliders, portfolios, testimonials, and more.

## 📑 Index

1. [MainDemo.jsx](#maindemojsx)
    - [Purpose](#purpose-1)
    - [Structure and Components](#structure-and-components-1)
2. [PortfolioLanding.jsx](#portfoliolandingjsx)
    - [Purpose](#purpose-2)
    - [Structure and Components](#structure-and-components-2)

---

## MainDemo.jsx

### Purpose

The **MainDemo.jsx** file is a React component that serves as a template for a dark-themed landing page. It integrates various components to display a slider, about section, services, portfolio, counters, testimonials, blog section, and brand logos. This file provides a comprehensive view of the company's or individual's offerings and achievements.

### Structure and Components

Here's a breakdown of the components used in **MainDemo.jsx**:

| Component | Description |
|-----------|-------------|
| `Helmet` | Manages the document head, setting the page title to "Main Demo Dark". |
| `Header` | Displays the navigation bar with options for transparency and dark color themes. |
| `SliderOne` | Adds a slider to showcase featured content at the top of the page. |
| `About` | Introduces the company or individual with a brief description. |
| `ServiceTwo` | Highlights services offered. |
| `Portfolio` | Displays a carousel of projects or work. |
| `CounterOne` | Shows fun facts or statistics using animated counters. |
| `Testimonial` | Presents client testimonials. |
| `BlogContent` | Lists the latest blog posts. |
| `BrandTwo` | Shows a gallery of brand logos associated with the company. |
| `ScrollToTop` | Provides a button to scroll back to the top of the page. |
| `Footer` | Concludes the page with additional navigation and contact information. |

Here is a sample code snippet from the file:

```jsx
<div className="backto-top">
    <ScrollToTop showUnder={160}>
        <FiChevronUp />
    </ScrollToTop>
</div>
```

This snippet represents the "Back to Top" button functionality.

---

## PortfolioLanding.jsx

### Purpose

The **PortfolioLanding.jsx** file is another React component focusing on a personal portfolio page. It highlights personal achievements, services, projects, blog posts, and provides a contact section for potential clients or employers.

### Structure and Components

Here's a detailed breakdown of the components used in **PortfolioLanding.jsx**:

| Component | Description |
|-----------|-------------|
| `Helmet` | Sets the page title to "Portfolio Landing". |
| `HeaderThree` | A different styled header with home and logo links. |
| `TextLoop` | Animates texts for dynamic content presentation. |
| `TabTwo` | Displays tabbed content, useful for organizing information. |
| `ContactThree` | Provides a contact section with an image and title, "Hire Me". |
| `PortfolioList` | Lists portfolio items in a grid layout. |
| `ServiceList` | Displays services offered in a creative style. |
| `BlogContent` | Lists the latest blog posts. Similar to `MainDemo.jsx`. |
| `ScrollToTop` | Similar functionality to MainDemo, with a button to return to the top. |
| `FooterTwo` | Ends the page with navigation and contact details. |

Below is a sample from the file showcasing the integration of the `TextLoop` component:

```jsx
<h1 className="title">
    Hi, I’m Jone Doe <br />
    <TextLoop>
        <span> JS Developer.</span>
        <span> UI/UX Designer.</span>
        <span> Content Writer.</span>
    </TextLoop>{" "}
</h1>
```

This snippet animates the professional roles of the person, making the introduction lively and engaging.

---

Both files utilize React's component-based architecture to create structured, reusable, and maintainable web pages. They integrate various third-party libraries for icons, animations, and other UI elements to enhance the user experience. Feel free to explore and customize these templates to fit your needs! 🎨✨