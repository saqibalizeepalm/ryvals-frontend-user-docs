# 📄 Authentication Module Documentation

Welcome to the documentation for the authentication module comprising various React components for handling user authentication processes like login, signup, password reset, and more. This documentation will guide you through the code and functionalities of each component.

## 📑 Index

1. [Auth Wrapper](#auth-wrapper)
2. [Account Verification](#account-verification)
3. [Forget Password](#forget-password)
4. [Change Password](#change-password)
5. [Logout](#logout)
6. [Login](#login)
7. [Register](#register)
8. [Reset Password Request Successful](#reset-password-request-successful)
9. [Signup Successful](#signup-successful)
10. [Reset Password](#reset-password)

---

## 🎨 Auth Wrapper

**File Name:** `auth-wrapper.jsx`

### Description

The `AuthWrapper` component is responsible for rendering a background slider with parallax effects for authentication pages. It dynamically changes the background based on the route (`/signin` or `/signup`).

### Code Overview

- **Imports**: Uses React, Parallax, and Slider components.
- **Slider Configuration**: Utilizes an array `SlideList` to configure slide properties like `bgImage`, `title`, and `category`.
- **Conditional Rendering**: Changes slides based on the `queryString` from props.

**Example Usage:**

```jsx
<AuthWrapper data={props} />
```

---

## 📩 Account Verification

**File Name:** `account-verification.jsx`

### Description

Handles the account verification process post-signup via email verification links. It allows users to request a new verification email if the link has expired.

### Code Overview

- **State Management**: Manages states for loader, success, and email sent status.
- **Validation**: Uses `Yup` for form validation.
- **APIs**: Calls `verifyaccount` and `requestverification` functions from `authService`.

**Features:**

- Loader animation while verifying.
- Alert messages for success and errors.
- Resend verification email functionality.

**Example Usage:**

```jsx
<AccountVerification />
```

---

## 🔑 Forget Password

**File Name:** `forget-password.jsx`

### Description

This component allows users to request a password reset or retrieve their username via email.

### Code Overview

- **Form Handling**: Utilizes `react-hook-form` and `Yup` for validation.
- **Conditional Logic**: Determines if the request is for forgotten username or password.
- **APIs**: Uses `forgotpassword` and `forgotusername` functions.

**Features:**

- Displays loaders during API calls.
- Error handling and display.
- Toast notifications for success.

**Example Usage:**

```jsx
<ForgotPassword />
```

---

## 🔄 Change Password

**File Name:** `change-password.jsx`

### Description

Allows users to change their password via a form. This component is more of a placeholder as it lacks backend integration.

### Code Overview

- **State Management**: Manages form input states for password fields.
- **UI Elements**: Simple form structure with input fields for new and confirmed passwords.

**Example Usage:**

```jsx
<ChangePassword />
```

---

## 🚪 Logout

**File Name:** `Logout.jsx`

### Description

Handles user logout functionality. It clears user session data and redirects to the home page.

### Code Overview

- **State Management**: Uses `useDispatch` from Redux to dispatch logout actions.
- **Immediate Effect**: Calls logout functions on component mount via `useEffect`.

**Example Usage:**

```jsx
<Logout />
```

---

## 🔐 Login

**File Name:** `login.jsx`

### Description

Handles user login with options for social logins (Facebook, Google, Discord, etc.) and remembers user details if opted.

### Code Overview

- **Form Handling**: Uses `react-hook-form` for form state management and `Yup` for validation.
- **Social Logins**: Integrates with social platforms for OAuth login.
- **State Management**: Handles multiple states for loader, errors, and remember-me functionality.
- **APIs**: Uses `login`, `facebookLogin`, `googleLogin`, etc.

**Features:**

- Error messages and loading indicators.
- Social login options.
- Resend verification link if needed.

**Example Usage:**

```jsx
<Login />
```

---

## 📝 Register

**File Name:** `register.jsx`

### Description

Allows new users to register by providing necessary details, with options for social sign-up integrations.

### Code Overview

- **Form Handling**: Uses `react-hook-form` with `Yup` validation.
- **Social Sign-Up**: Supports OAuth via Facebook, Google, Twitter, Discord, and Twitch.
- **Age Verification**: Checks if the user is 18 or older.
- **State Management**: Manages states for form fields, errors, and loading.

**Features:**

- Password strength meter.
- Terms and conditions acceptance.
- Social sign-up and referral handling.

**Example Usage:**

```jsx
<Register />
```

---

## ✅ Reset Password Request Successful

**File Name:** `reset-password-request-successful.jsx`

### Description

Displays a confirmation message when a password reset email request is successful.

### Code Overview

- **Static Message**: Shows a static confirmation message with a link to check the email.

**Example Usage:**

```jsx
<ResetPasswordSuccess />
```

---

## 🌟 Signup Successful

**File Name:** `signup-successful.jsx`

### Description

Informs users of successful signup and prompts them to verify their email.

### Code Overview

- **Email Masking**: Masks part of the email for privacy.
- **Resend Verification**: Allows users to resend verification email.

**Example Usage:**

```jsx
<SignUpSuccess />
```

---

## 🔄 Reset Password

**File Name:** `reset-password.jsx`

### Description

Allows users to reset their password using a valid link received in their email.

### Code Overview

- **Form Handling**: Utilizes `react-hook-form` with `Yup` for validation.
- **APIs**: Calls `resetpassword` from `authService`.

**Features:**

- Password and confirm password fields.
- Shows loaders and error messages.

**Example Usage:**

```jsx
<ResetPassword />
```

---

This documentation aims to provide a comprehensive understanding of each component's functionality, how they interact with services, and how they can be used within your application. Happy coding! 🚀