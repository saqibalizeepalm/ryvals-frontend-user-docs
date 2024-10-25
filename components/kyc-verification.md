# KYC Verification Component Documentation 📜

This documentation provides a comprehensive overview of the `KycVerification.jsx` file, explaining its purpose, functionality, and usage. This file is a React component designed to facilitate Know Your Customer (KYC) verification in a web application.

---

## Index 📑

1. [Introduction](#introduction-)
2. [Component Overview](#component-overview-)
3. [Props](#props-)
4. [Environment Variables](#environment-variables-)
5. [Component Structure](#component-structure-)
6. [Usage](#usage-)
7. [Conclusion](#conclusion-)

---

## Introduction 🌟

**KYC Verification** is an essential process used by organizations to verify the identity of their users. This component is built using React and leverages the `react-bootstrap` library for modal functionality. It provides a user interface for ID verification by displaying a modal with a QR code and a link for verification.

## Component Overview 🛠️

The `KycVerification` component is a functional React component that renders a modal for KYC purposes. It includes:

- A header with the title "ID Verification".
- A body that contains instructions and a QR code for the user to scan.
- A link to an external URL for ID verification.

## Props 🏷️

This component accepts the following props:

| Prop Name  | Type   | Description                            |
|------------|--------|----------------------------------------|
| `subheader`| string | Additional information for the header. |

**Note:** The `subheader` prop is optional and is used to dynamically display information within the component.

## Environment Variables 🌍

The component relies on several environment variables to fetch dynamic content. These variables include:

- **`REACT_APP_ID_MISSION_QR`**: The URL for the QR code image.
- **`REACT_APP_ID_MISSION_URL`**: The URL for the ID verification link.

These variables should be defined in your environment configuration to ensure the component functions correctly.

## Component Structure 🏗️

Here's a breakdown of the component's structure and functionality:

```jsx
import React from "react";
import { Modal } from "react-bootstrap";
import PropTypes from "prop-types";

const KycVerification = (props) => {
    console.log(process.env.REACT_APP_ID_MISSION_QR);

    return (
        <>
            <Modal.Header closeButton>
                <Modal.Title>ID Verification</Modal.Title>
            </Modal.Header>
            <Modal.Body className="qr-verification-body">
                <p>
                    In order to {props.subheader} player needs to verify identification
                </p>
                <h4>Get yourself verified</h4>
                <h5>
                    <a href={process.env.REACT_APP_ID_MISSION_URL} target="_blank" rel="noopener noreferrer">
                        {process.env.REACT_APP_ID_MISSION_URL}
                    </a>
                </h5>
                <p>or</p>
                <h6>Scan QR code:</h6>
                <div className="qr-code">
                    <img
                        src={process.env.REACT_APP_ID_MISSION_QR}
                        alt="qr"
                        width={200}
                    />
                </div>
            </Modal.Body>
        </>
    );
};

KycVerification.propTypes = {
    subheader: PropTypes.string,
};

export default KycVerification;
```

**Key Points:**

- The component uses `react-bootstrap`'s `Modal` component to create a popup interface.
- The `subheader` prop is used to personalize the verification message.
- The QR code and link are dynamically retrieved from environment variables.

## Usage 🚀

To use the `KycVerification` component in your React application, ensure you have the necessary environment variables set up. Then, import and integrate the component as shown below:

```jsx
import KycVerification from './KycVerification';

function App() {
    return (
        <div className="App">
            <KycVerification subheader="access additional features" />
        </div>
    );
}

export default App;
```

**Steps:**
1. Import the `KycVerification` component.
2. Use it within your application's component tree.
3. Pass the `subheader` prop if needed to customize the user message.

## Conclusion 🎉

The `KycVerification.jsx` component is a well-structured and easy-to-use module for implementing KYC verification in a React application. By leveraging environment variables, it allows for flexibility and adaptability in different deployment settings. This component serves as a crucial part of identity verification, ensuring compliance and enhancing user trust in your platform.