# FAQ Service Documentation 📚

Welcome to the **FAQ Service** documentation! This module is designed to handle API requests related to Frequently Asked Questions and feedback submissions. It leverages Axios for HTTP requests and integrates with an authentication system to ensure secure access. Let's dive into its functionalities and usage.

## Table of Contents
1. [Introduction](#introduction)
2. [Setup](#setup)
3. [Functions Overview](#functions-overview)
   - [`faqlisting`](#faqlisting)
   - [`sendFeedBack`](#sendfeedback)
4. [Error Handling](#error-handling)
5. [Authentication Token](#authentication-token)

## Introduction

The **FAQ Service** provides functionalities to:
- Fetch a list of FAQs from the server.
- Send user feedback to the server.

This service is crucial for maintaining user engagement and support through easy access to information and feedback mechanisms.

## Setup

Before using the FAQ Service, ensure that you have the following environment variables set up:

- `REACT_APP_APIURL`: The base URL for the API endpoints.

Additionally, ensure that your project has the following dependencies:

```bash
npm install axios
```

## Functions Overview

### `faqlisting`

**Description**: Fetches the list of Frequently Asked Questions from the server.

- **Endpoint**: `/pages/faqs/`
- **Method**: `GET`
- **Headers**:
  - `Content-Type: application/json`
  - Authorization token (added by `passAuthToken()`)

**Usage**:

```javascript
import { faqlisting } from './faq.service';

async function fetchFAQs() {
  try {
    const faqs = await faqlisting();
    console.log('FAQs:', faqs);
  } catch (error) {
    console.error('Error fetching FAQs:', error);
  }
}

fetchFAQs();
```

### `sendFeedBack`

**Description**: Sends user feedback to the server.

- **Endpoint**: `/emails/feedback/`
- **Method**: `POST`
- **Headers**:
  - `Content-Type: application/json`
  - Authorization token (added by `passAuthToken()`)
- **Body**: JSON object containing feedback details.

**Usage**:

```javascript
import { sendFeedBack } from './faq.service';

async function submitFeedback(feedbackData) {
  try {
    const response = await sendFeedBack(feedbackData);
    console.log('Feedback submitted successfully:', response);
  } catch (error) {
    console.error('Error submitting feedback:', error);
  }
}

const feedbackData = {
  message: "Great service!",
  user_email: "user@example.com",
};

submitFeedback(feedbackData);
```

## Error Handling

The service uses Axios interceptors to handle errors. Common status codes and their actions include:

- **401 Unauthorized**: Redirects to the `/logout` page.
- **406 Not Acceptable**: Redirects to the `/vpn` page.
- For other errors, it constructs a detailed error message by iterating over the response data.

## Authentication Token

The `passAuthToken` function ensures that each request includes the necessary authorization token. It sets the `Authorization` header with the token retrieved from the `AuthToken` helper.

```javascript
function passAuthToken() {
  axiosApi.defaults.headers.common["Authorization"] = AuthToken();
}
```

This helper function is crucial for maintaining secure access to the FAQ endpoints.

---

Thank you for using the **FAQ Service**! If you have any questions or need further assistance, feel free to reach out. Happy coding! 🚀