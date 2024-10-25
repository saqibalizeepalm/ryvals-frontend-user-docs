# 📄 Documentation for Ryvals Legal Pages

## Table of Contents
1. [Introduction](#introduction)
2. [PrivacyPolicy.jsx](#privacypolicyjsx)
   - [Overview](#overview)
   - [Key Components](#key-components)
   - [Functionality](#functionality)
3. [CaliforniaPrivacy.jsx](#californiaprivacyjsx)
   - [Overview](#overview)
   - [Key Components](#key-components)
   - [Functionality](#functionality)
4. [TermsOfUse.jsx](#termsofusejsx)
   - [Overview](#overview)
   - [Key Components](#key-components)
   - [Functionality](#functionality)
5. [Conclusion](#conclusion)

## Introduction

This documentation provides an in-depth look into three React components—`PrivacyPolicy.jsx`, `CaliforniaPrivacy.jsx`, and `TermsOfUse.jsx`—used for displaying legal information on the Ryvals website. These components utilize React, Bootstrap, and other libraries to create an engaging and informative user interface for legal documentation.

---

## PrivacyPolicy.jsx

### Overview

The `PrivacyPolicy.jsx` file is a React component responsible for displaying the privacy policy of Ryvals. It fetches and renders the privacy policy content from a CMS (Content Management System) and displays it to the user.

### Key Components

- **React & React Hooks**: Utilizes `useState` and `useEffect` to manage component state and lifecycle.
- **Parallax**: Creates a parallax scrolling effect using the `react-parallax` library.
- **Bootstrap Placeholder**: Displays a loading animation while the content is being fetched.
- **CMS Data Fetching**: Retrieves content from a CMS service.

### Functionality

- **State Management**: 
  - `loading`: A boolean flag to indicate if the content is still being fetched.
  - `privacyData`: Stores the content fetched from the CMS.
  
- **useEffect Hook**: 
  - Triggers content fetching on component mount.
  - Sets `loading` to `true` before fetching and `false` afterward.

- **Rendering**:
  - Displays a parallax header with a title "Ryvals Privacy Policy".
  - Shows the policy content fetched from the CMS.
  - Uses Bootstrap `Placeholder` for loading animation if content is not ready.

```jsx
import React, { useState, useEffect } from "react";
import { Parallax } from "react-parallax";
import { Placeholder } from "react-bootstrap";
import { getCMSData } from "../../services/cms.service";

const PrivacyPolicy = () => {
  // State hooks for loading and privacy data
  const [loading, setLoading] = useState(false);
  const [privacyData, setPrivacyDatas] = useState("");

  // Fetch data from CMS on component mount
  useEffect(() => {
    setLoading(true);
    let body = { title: "privacy-policy" };
    getCMSData(body).then((res) => {
      setLoading(false);
      setPrivacyDatas(res);
    });
  }, []);

  return (
    <>
      {/* Parallax header */}
      <div className="slider-activation slider-creative-agency profile-slider">
        <Parallax bgImage={"/assets/images/header-background.png"} strength={500} bgClassName="page-banner-parallax">
          <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="inner text-center">
                    <h1 className="title game-title theme-gradient privacy-policy">
                      Ryvals Privacy Policy
                    </h1>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </Parallax>
      </div>

      {/* Privacy Policy Content or Placeholder */}
      {!loading ? (
        <section className="privacy-policy-section">
          <div className="container">
            <div className="row">
              <div className="col">
                <p dangerouslySetInnerHTML={{ __html: privacyData.content }}></p>
              </div>
            </div>
          </div>
        </section>
      ) : (
        <section className="privacy-policy-section">
          <div className="container">
            <div className="row">
              <div className="col">
                <p>
                  <Placeholder animation="glow">
                    <Placeholder xs={7} /> <Placeholder xs={4} /> <Placeholder xs={4} /> <Placeholder xs={6} /> <Placeholder xs={8} />
                  </Placeholder>
                </p>
              </div>
            </div>
          </div>
        </section>
      )}
    </>
  );
};

export default PrivacyPolicy;
```

---

## CaliforniaPrivacy.jsx

### Overview

The `CaliforniaPrivacy.jsx` file is a React component that outlines privacy policies specific to California residents in compliance with the California Consumer Privacy Act (CCPA).

### Key Components

- **React Component Class**: Unlike the previous file, this component uses a class-based approach.
- **Parallax**: Uses the `react-parallax` for a dynamic header effect.
- **React-Bootstrap Table**: Displays tabular data regarding personal information categories, examples, and recipients.

### Functionality

- **Static Header**: Displays a parallax header with the title "California Consumer Privacy Notice".
  
- **Content Sections**:
  - Detailed explanation of privacy practices in accordance with the CCPA.
  - Sections include categories of personal information, sources, purposes, rights, and notices specific to California.

- **Table Display**: 
  - Information about categories of Personal Information (PI), examples, and recipients shared with.
  
- **Rights and Notices**:
  - Explains California consumers' rights under the CCPA.
  - Provides contact information for privacy inquiries.

```jsx
import React, { Component } from "react";
import { Parallax } from "react-parallax";
import Table from "react-bootstrap/Table";

class CaliforniaPrivacy extends Component {
  render() {
    return (
      <>
        {/* Parallax header */}
        <div className="slider-activation slider-creative-agency profile-slider">
          <Parallax bgImage={"/assets/images/header-background.png"} strength={500} bgClassName="page-banner-parallax">
            <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
              <div className="container">
                <div className="row">
                  <div className="col-lg-12">
                    <div className="inner text-center">
                      <h1 className="title game-title theme-gradient privacy-policy california-title">
                        California Consumer <span>Privacy Notice</span>
                      </h1>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </Parallax>
        </div>

        {/* Content Section */}
        <section className="california">
          <div className="container">
            <div className="row">
              <div className="col">
                <h2>Effective Date: May 15, 2021</h2>
                {/* Content explaining CCPA compliance */}
                <p>
                  This California Consumer Privacy Notice (“Notice”) applies to Ryvals, Inc. and ...
                </p>
                <ul className="upper-greek">
                  <li>
                    <b>PI We Collect</b>
                    <ul className="upper-alpha">
                      <li>
                        <u>Categories</u>
                        <p>
                          <Table>
                            <thead>
                              <tr>
                                <th>Category of PI</th>
                                <th>Examples of PI</th>
                                <th>Categories of Recipients with whom PI is Shared</th>
                              </tr>
                            </thead>
                            <tbody>
                              <tr>
                                <td>1. Identifiers</td>
                                <td>...<td>
                                <td>...</td>
                              </tr>
                              {/* Other categories */}
                            </tbody>
                          </Table>
                        </p>
                      </li>
                      {/* Other sections */}
                    </ul>
                  </li>
                  <li>
                    <b>Sharing of PI</b>
                    <p>...</p>
                  </li>
                  <li>
                    <b>Your California Privacy Rights</b>
                    <p>...</p>
                  </li>
                  <li>
                    <b>Additional California Notices</b>
                    <p>...</p>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </section>
      </>
    );
  }
}

export default CaliforniaPrivacy;
```

---

## TermsOfUse.jsx

### Overview

The `TermsOfUse.jsx` file is a React component that renders the terms and conditions for using Ryvals services, similar in structure and functionality to the `PrivacyPolicy` component.

### Key Components

- **React Hooks**: Uses `useState` and `useEffect` for state management and lifecycle control.
- **Parallax**: Provides an engaging header using the `react-parallax` library.
- **CMS Data Fetching**: Retrieves and displays terms and conditions from a CMS.

### Functionality

- **State Management**:
  - `loading`: Indicates whether the terms data is being fetched.
  - `termsAndCondition`: Stores the terms and conditions content fetched from the CMS.
  
- **useEffect Hook**: 
  - Fetches data from the CMS when the component is mounted.
  - Manages loading state during the data retrieval process.

- **Rendering**:
  - Displays a header with "Ryvals Terms Of Use".
  - Renders the terms and conditions content or a loading placeholder.

```jsx
import React, { useState, useEffect } from "react";
import { Parallax } from "react-parallax";
import { Placeholder } from "react-bootstrap";
import { getCMSData } from "../../services/cms.service";

const TermsOfUse = () => {
  // State hooks for loading and terms data
  const [loading, setLoading] = useState(false);
  const [termsAndCondition, setTermsAndConditions] = useState("");

  // Fetch data from CMS on component mount
  useEffect(() => {
    setLoading(true);
    let body = { title: "terms-and-conditions" };
    getCMSData(body).then((res) => {
      setLoading(false);
      setTermsAndConditions(res);
    });
  }, []);

  return (
    <>
      {/* Parallax header */}
      <div className="slider-activation slider-creative-agency profile-slider">
        <Parallax bgImage={"/assets/images/header-background.png"} strength={500} bgClassName="page-banner-parallax">
          <div className="slide slide-style-2 game-slide slider-paralax d-flex align-items-center justify-content-center">
            <div className="container">
              <div className="row">
                <div className="col-lg-12">
                  <div className="inner text-center">
                    <h1 className="title game-title theme-gradient privacy-policy">
                      Ryvals Terms Of Use
                    </h1>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </Parallax>
      </div>

      {/* Terms of Use Content or Placeholder */}
      {!loading ? (
        <section className="terms-of-use">
          <div className="container">
            <div className="row">
              <div className="col">
                <p dangerouslySetInnerHTML={{ __html: termsAndCondition.content }}></p>
              </div>
            </div>
          </div>
        </section>
      ) : (
        <section className="privacy-policy-section">
          <div className="container">
            <div className="row">
              <div className="col">
                <p>
                  <Placeholder animation="glow">
                    <Placeholder xs={7} /> <Placeholder xs={4} /> <Placeholder xs={4} /> <Placeholder xs={6} /> <Placeholder xs={8} />
                  </Placeholder>
                </p>
              </div>
            </div>
          </div>
        </section>
      )}
    </>
  );
};

export default TermsOfUse;
```

---

## Conclusion

These components are essential for providing legal transparency to users of the Ryvals platform. They leverage React's component-based architecture to fetch and display dynamic content from a CMS, ensuring that users always have access to the latest legal information. The use of parallax effects and Bootstrap enhances the user experience while maintaining a professional presentation.