# RedeemFunds.jsx Documentation 📄✨

Welcome to the documentation for the **RedeemFunds.jsx** file. This React component is designed to allow users to redeem funds from their wallet through a modal interface. The component checks the user's KYC (Know Your Customer) status and validates the redeem request before processing.

## Index

1. [Component Overview](#component-overview)
2. [Imports and Dependencies](#imports-and-dependencies)
3. [State Variables](#state-variables)
4. [Effects and Functions](#effects-and-functions)
5. [Validation Schema](#validation-schema)
6. [Form Handling](#form-handling)
7. [Render Logic](#render-logic)
8. [PropTypes](#proptypes)

---

## Component Overview

The **RedeemFunds** component provides a modal interface for users to redeem funds from their wallet balance. It ensures that the user has completed KYC verification and validates the amount to be redeemed before proceeding with the transaction.

## Imports and Dependencies

**Libraries and Frameworks Used:**

- **React**: The component is built using the React library.
- **React Bootstrap**: Modal, Form, Button, Placeholder, and InputGroup components are used for UI elements.
- **React Hook Form**: Used for form handling.
- **Yup**: Utilized for validation schema.
- **PropTypes**: Used to type-check the properties passed to the component.

**Code Block:**

```javascript
import React, { useEffect, useState } from "react";
import { Modal, Form, Button, Placeholder, InputGroup } from "react-bootstrap";
import { getKycStatus, redeemAmount } from "../../services/user.service";
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as Yup from "yup";
import PropTypes from "prop-types";
import KycVerification from "../kyc-verification/KycVerification";
```

## State Variables

The component uses several state variables to manage its logic:

- **iskycDone**: Tracks if KYC is completed. (Boolean)
- **iskycStatusLoading**: Indicates if KYC status is being loaded. (Boolean)
- **isLoading**: Flag for loading state during the redeem process. (Boolean)
- **isRedeemProcessDone**: Checks if the redeem process has been completed. (Boolean)
- **deductedAmount**: Stores the amount deducted during the redeem process. (Number)
- **updatedWallet**: Holds the updated wallet balance after the transaction. (Number)

## Effects and Functions

### useEffect Hook

On component mount, it invokes the **checkUserKyc** function to fetch the user's KYC status.

```javascript
useEffect(() => {
  checkUserKyc();
}, []);
```

### Functions

- **checkUserKyc**: Asynchronously fetches and updates the user's KYC status.
- **onRedeemMoney**: Handles the redeem process, making an asynchronous call to the redeem service and updates the state based on the outcome.

## Validation Schema

A Yup validation schema is defined to ensure the correctness of input data:

- **paypal**: Must be a string and is required.
- **amount**: Must be a number, greater than or equal to $5, less than or equal to the wallet balance, and formatted correctly.

**Code Block:**

```javascript
const validationSchema = Yup.object().shape({
  paypal: Yup.string()
    .typeError("PayPal id is required, please add it first from edit profile")
    .required("PayPal id is required, please add it first from edit profile"),
  amount: Yup.number()
    .typeError("it must specify a number")
    .min(5, "Amount has to be more than $5 or $5")
    .max(+props.wallet_balance, `Amount has to be less than $${props.wallet_balance}`)
    .positive("Amount cannot be 0")
    .test("invalid-decimal", "Amount doesn't have more than 2 decimal points", 
      (value) => (value + "").match(/^(\d+(\.\d{1,2})?)$/))
    .required("Amount is required"),
});
```

## Form Handling

**React Hook Form** is used along with the Yup resolver for handling form submissions and validations.

**Code Block:**

```javascript
const { register, handleSubmit, formState: { errors } } = useForm({
  defaultValues: { paypal: props.paypal_id },
  resolver: yupResolver(validationSchema),
});
```

## Render Logic

The component conditionally renders different UI elements based on the user's KYC status, loading states, and whether the redeem process is complete:

1. **Loading State**: Shows placeholders while loading KYC status.
2. **KYC Incomplete**: Displays a KYC verification component if the user hasn't completed KYC.
3. **Redeem Form**: Displays a form allowing users to enter the amount to redeem.
4. **Redeem Success**: Shows a success message and updated wallet balance once funds are redeemed.

**Code Block:**

```jsx
return (
  <>
    {iskycStatusLoading ? (
      // Loading placeholders
    ) : !isRedeemProcessDone ? (
      !iskycDone ? (
        <KycVerification subheader={"reedem funds"} />
      ) : (
        // Redeem form
      )
    ) : (
      // Success message
    )}
  </>
);
```

## PropTypes

The component uses **PropTypes** to validate the types of props passed to it, ensuring correct usage:

| Prop        | Type   | Description                  |
|-------------|--------|------------------------------|
| wallet_balance | String | The user's available wallet balance. |
| paypal_id   | String | The user's PayPal ID.        |

**Code Block:**

```javascript
RedeemFunds.propTypes = {
  wallet_balance: PropTypes.string,
  paypal_id: PropTypes.string,
};
```

---

This concludes the documentation for the **RedeemFunds.jsx** component. This component plays a crucial role in enabling users to redeem their funds securely, ensuring all necessary checks and validations are performed. If you have further questions, feel free to ask! 😊