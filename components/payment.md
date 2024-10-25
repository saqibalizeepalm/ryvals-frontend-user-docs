# 📚 Documentation for AddToWallet.jsx and StripeForm.js

## 📜 Index

1. [Introduction](#introduction)
2. [AddToWallet.jsx](#addtowalletjsx)
   - [Overview](#overview)
   - [Key Functionalities](#key-functionalities)
   - [Code Breakdown](#code-breakdown)
   - [PropTypes](#proptypes)
3. [StripeForm.js](#stripeformjs)
   - [Overview](#overview-1)
   - [Key Functionalities](#key-functionalities-1)
   - [Code Breakdown](#code-breakdown-1)
   - [PropTypes](#proptypes-1)

---

## 🌟 Introduction

This documentation aims to provide a comprehensive understanding of two key components in a React application: `AddToWallet.jsx` and `StripeForm.js`. These components are integral to managing user transactions and wallet functionalities using Stripe service for payment processing.

---

## 💳 AddToWallet.jsx

### Overview

The **AddToWallet.jsx** component is designed to facilitate the addition of funds to a user's digital wallet. It handles user interactions, validates input amounts, checks KYC (Know Your Customer) status, and navigates to the payment page.

### Key Functionalities

- **KYC Status Check**: Verifies if the user has completed KYC requirements.
- **Public Key Retrieval**: Fetches the public key from Stripe for secure transactions.
- **Amount Validation**: Ensures entered amounts are valid, following specific rules (e.g., minimum and maximum limits).
- **Navigation**: Redirects users to appropriate pages based on their current path and transaction details.

### Code Breakdown

#### 1. **Imports and Initial Setup**
```jsx
import React, { useState, useEffect } from "react";
import { Button, Modal, Placeholder, Form, InputGroup } from "react-bootstrap";
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as Yup from "yup";
import { getKycStatus, getPublicKeyStripe } from "../../services/user.service.js";
import PropTypes from "prop-types";
import { withRouter } from "react-router-dom";
```
- **React Hooks**: Utilized for managing component state and lifecycle.
- **React-Bootstrap**: Provides UI components like Modals and Forms.
- **Yup and React Hook Form**: Used for form validation.
- **Service Functions**: `getKycStatus` and `getPublicKeyStripe` are async functions that interact with backend services.

#### 2. **Component State and Effects**
```jsx
const [publicKey, setPublicKey] = useState("");
const [iskycDone, setiskycDone] = useState(false);
const [iskycStatusLoading, setiskycStatusLoading] = useState(false);
const [isLoading, setisLoading] = useState(false);

useEffect(() => {
  checkUserKyc();
  getPublicKey();
}, []);
```
- **State Variables**: Manage public key, KYC status, and loading states.
- **useEffect**: Triggers initial data fetching for KYC status and public key when the component mounts.

#### 3. **Validation Schema**
```jsx
const validationSchema = Yup.object().shape({
  amount: Yup.number()
    .typeError("it must specify a number")
    .required("Amount is required")
    .positive("Amount cannot be 0")
    .min(10, "Amount has to be more than $10")
    .max(10000, "Amount would not be greater than $10,000")
    .test("invalid-decimal", "Amount doesn't have more than 2 decimal points", (value) => (value + "").match(/^(\d+(\.\d{1,2})?)$/)),
});
```
- **Validation Rules**: Enforces numeric input, positivity, range limits, and decimal precision.

#### 4. **Form Handling and Submission**
```jsx
const { register, handleSubmit, formState: { errors } } = useForm({
  defaultValues: { amount: props.prevAmount },
  resolver: yupResolver(validationSchema),
});

const onSubmit = (data) => {
  // Navigate to the appropriate route with payment details
};
```

### PropTypes

- **closeModal**: Function to close the modal window.

```jsx
AddToWallet.propTypes = {
  closeModal: PropTypes.func,
};
```

---

## 💸 StripeForm.js

### Overview

The **StripeForm.js** component is responsible for processing payment details using the Stripe API. It handles user input for billing information, validates the data, and performs the transaction.

### Key Functionalities

- **Stripe Integration**: Connects with Stripe to handle secure payment processing.
- **Form Validation**: Ensures user inputs are complete and correct.
- **Dynamic Country and State Selection**: Loads and displays country and state options based on user selection.
- **Transaction Completion**: Finalizes and confirms the payment, updating the user's wallet balance.

### Code Breakdown

#### 1. **Imports and Initial Setup**
```jsx
import React, { useState, useEffect } from "react";
import { withRouter, useHistory } from "react-router-dom";
import { Elements, CardElement, useElements, useStripe } from "@stripe/react-stripe-js";
import { loadStripe } from "@stripe/stripe-js";
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as Yup from "yup";
```
- **Stripe Elements**: Used for creating secure card input fields.
- **React Router**: Navigates between routes.
- **Validation Libraries**: Maintain consistent validation logic.

#### 2. **State and Effects**
```jsx
const [countries, setCountries] = useState([]);
const [states, setStates] = useState([]);
const [isLoading, setisLoading] = useState(false);

useEffect(() => {
  getCountries().then((res) => setCountries(res));
}, []);
```
- **State Variables**: Track loading, country, and state information.
- **Data Fetching**: Retrieves a list of countries when the component mounts.

#### 3. **Form Validation and Submission**
```jsx
const validationSchema = Yup.object().shape({
  email: Yup.string().trim().required("Email is required"),
  addressLine1: Yup.string().trim().required("Address line 1 is required"),
  city: Yup.string().trim().required("City is required"),
  states: Yup.string().required("State is required"),
  country: Yup.string().required("Country is required"),
  postalCode: Yup.string().trim().required("Postal Code is required"),
});

const { register, handleSubmit, formState: { errors } } = useForm({
  resolver: yupResolver(validationSchema),
});

async function onSubmit(dataCard) {
  // Process the payment using Stripe
}
```
- **Validation Schema**: Ensures all required fields are filled.
- **onSubmit Function**: Handles the process of creating a token and submitting payment to the server.

#### 4. **UI and Elements**
```jsx
<Button disabled={!stripe || !elements || isLoading} variant="primary" type="submit">
  {isLoading ? "Please wait" : `Pay $${fees}`}
</Button>
```
- **Conditional Rendering**: Disables button while processing and shows loading state.

### PropTypes

- **Stripe Key**: Required for initializing Stripe Elements.

```jsx
StripeForm.propTypes = {
  location: PropTypes.object.isRequired,
};
```

---

By understanding the components and functionalities described above, developers can effectively maintain and extend the functionalities of the `AddToWallet.jsx` and `StripeForm.js` components. These components together facilitate a secure and user-friendly experience for managing wallet transactions using Stripe.