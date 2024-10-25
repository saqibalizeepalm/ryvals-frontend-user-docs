# 📚 Project Documentation

Welcome to the documentation for the **FAQ** and **PPK** components of our React application! This document will guide you through the structure and purpose of each component file. Let's dive into the specifics of each file!

---

## 📑 Index

1. [FAQ.jsx](#faqjsx)
   - [Overview](#overview)
   - [Key Features](#key-features)
   - [Detailed Breakdown](#detailed-breakdown)
   - [Visual Structure](#visual-structure)
2. [PPK.jsx](#ppkjsx)
   - [Overview](#overview-1)
   - [Key Features](#key-features-1)
   - [Detailed Breakdown](#detailed-breakdown-1)
   - [Visual Structure](#visual-structure-1)

---

## Faq.jsx

### Overview

The `Faq.jsx` component is a feature-rich FAQ section designed to provide answers to common questions users might have about the service or product. It includes a feedback mechanism, allowing users to submit their queries if their questions aren't covered in the FAQ section.

### Key Features

- **Parallax Background**: Adds a dynamic visual effect for the FAQ page.
- **Accordion for FAQs**: Uses Bootstrap components to display questions and answers in an expandable/collapsible format.
- **Feedback Modal**: A user-friendly form that allows users to submit questions or feedback directly from the FAQ page.
- **Form Validation**: Ensures that user inputs are validated using the Yup schema.
- **Phone Input**: A specialized input for phone numbers with international support.
- **Dynamic FAQ Loading**: Fetches FAQ data asynchronously and updates the UI accordingly.

### Detailed Breakdown

#### 1. **Imports and Initialization:**

```jsx
import React, { useState, useEffect } from "react";
import Accordion from "react-bootstrap/Accordion";
import { Button, Modal, Spinner, Form } from "react-bootstrap";
import { faqlisting, sendFeedBack } from "../../services/faq.service";
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as Yup from "yup";
import PhoneInput from "react-phone-input-2";
import toastify from "../../helper/toastify.jsx";
```

- **React and Hooks**: Utilizes React's `useState` and `useEffect` for state management and lifecycle methods.
- **Bootstrap Components**: For UI components such as Accordion and Modal.
- **Form Libraries**: `react-hook-form` for handling form state and validation with Yup.

#### 2. **State Management:**

- Manages various states including:
  - `openFeedback`: To control the visibility of the feedback modal.
  - `loading`: To display a loading spinner while fetching FAQs.
  - `faqs`: To store and display the list of FAQs.
  - `phoneNumber`, `countryCode`: For handling phone input.
  - `isSubmitDisabled`: To disable the submit button conditionally.

#### 3. **Effect Hooks and Functions:**

- **useEffect**: Fetches FAQ data on mount and listens for a logout event to reload the page.
- **getList**: Asynchronously fetches FAQ data and updates the state.

#### 4. **Rendering:**

- **Parallax and Title**: Displays a banner with a parallax effect for aesthetic appeal.
- **FAQ Section**: Renders FAQs in an accordion format.
- **Feedback Modal**: Provides a form for users to submit feedback.

### Visual Structure

```plaintext
<Parallax>
  <Modal> // Feedback Form
  <Accordion> // FAQ List
    <Accordion.Item> // FAQ Entry
```

---

## PPK.jsx

### Overview

The `PPK.jsx` component is focused on explaining the concept of PPK (Pay-Per-Kill), which is a unique online gaming tournament model. It uses the familiar FAQ format to answer common questions about PPK and its associated platform, Ryvals.com.

### Key Features

- **Parallax Background**: Similar to the FAQ component, it adds a visually appealing background.
- **Accordion for Content**: Uses Bootstrap's Accordion to organize information about PPK.
- **External Links**: Provides links to relevant external resources for more information.
- **List of Steps**: Detailed steps for users on how to participate in PPK tournaments.

### Detailed Breakdown

#### 1. **Imports and Initialization:**

```jsx
import React, { useEffect } from "react";
import Accordion from "react-bootstrap/Accordion";
import { Link } from "react-router-dom";
```

- **React and Hooks**: Uses `useEffect` for component lifecycle handling.
- **Bootstrap Components**: For organizing content in an accordion.
- **React Router**: For linking to external pages.

#### 2. **Effect Hooks:**

- **useEffect**: Listens for storage changes (e.g., logout event) to refresh the page.

#### 3. **Rendering:**

- **Parallax and Title**: Sets up a visually engaging header.
- **PPK Content**: Explains what PPK is and how it functions within the Ryvals platform.
- **Accordion Items**: Covers various FAQs about PPK, including how it works and how to join.

### Visual Structure

```plaintext
<Parallax>
  <Accordion>
    <Accordion.Item> // PPK FAQ Entry
```

---

## 🎨 Conclusion

Both **Faq.jsx** and **PPK.jsx** components are integral parts of the application, providing users with vital information and interactive features. The `Faq.jsx` focuses more on user interaction with feedback mechanisms, while `PPK.jsx` provides detailed explanations of the PPK model, ensuring users understand the unique aspects of the gaming platform. These components enhance user engagement and improve the overall user experience by enabling easy access to information.

💡 **Note:** Both components leverage Bootstrap for styling and React for dynamic content rendering, ensuring a responsive and interactive user interface.