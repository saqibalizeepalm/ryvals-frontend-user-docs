# 📚 Code Documentation

Welcome to the documentation for the various components involved in managing profiles and accounts within a user interface. Each component plays a unique role in handling different aspects of user profiles, settings, and related functionalities. This documentation aims to give you a comprehensive view of what each component does, how they interact, and their respective functionalities. 

## Index

1. [CheckProfileCompletion.js](#checkprofilecompletion-js)
2. [ChangePassword.js](#changepassword-js)
3. [EditGameName.jsx](#editgamename-jsx)
4. [EditPicture.jsx](#editpicture-jsx)
5. [EditProfile.jsx](#editprofile-jsx)
6. [GameAccount.jsx](#gameaccount-jsx)
7. [PaypalAccount.js](#paypalaccount-js)
8. [MyProfile.jsx](#myprofile-jsx)
9. [PlayerProfile.jsx](#playerprofile-jsx)

---

## CheckProfileCompletion.js

### 📄 Overview

- **Purpose**: This function checks whether a user’s profile is fully completed by verifying the presence of specific fields.
- **Usage**: It is used to determine if a user’s profile has all necessary information filled out.

### 💻 Code Explanation

```javascript
function CheckProfileCompletion(userInfo) {
  if (
    userInfo.firstname &&
    userInfo.lastName &&
    userInfo.street &&
    userInfo.city &&
    userInfo.state &&
    userInfo.postalCode &&
    userInfo.paypalId &&
    userInfo.discordId
  ) {
    // Profile is complete
  } else {
    // Profile is incomplete
  }
}

export default CheckProfileCompletion;
```

- The function takes `userInfo` as an argument and checks if all required fields are present.
- The presence of fields such as `firstname`, `lastName`, `street`, etc., implies a complete profile.

---

## ChangePassword.js

### 📄 Overview

- **Purpose**: This component provides a form for users to change their passwords.
- **Features**:
  - Password must meet specific criteria.
  - Shows password strength.
  - Includes form validation using Yup.

### 💻 Code Explanation

```javascript
// Imports and initial setup
import React, { useState } from "react";
import { useForm } from "react-hook-form";
import * as Yup from "yup";

// Component Function
const ChangePassword = () => {
  const [isLoading, setisLoading] = useState(false);

  // Validation Schema
  const validationSchema = Yup.object().shape({
    currentPassword: Yup.string().required("Current password is required"),
    password: Yup.string()
      .matches(
        /^(?=.*[\d])(?=.*[@$!%*#?&^_-])[A-Za-z\d@$!%*#?&^_-]{8,15}$/,
        "Password allows 8-15 alphanumeric characters with at least 1 digit and 1 special character [@$!%*#?&^_-]"
      ),
    confirmPassword: Yup.string().oneOf(
      [Yup.ref("password")],
      "Password and confirm password not matched"
    ),
  });

  // Form handling
  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(validationSchema),
  });

  // Submit handler
  const onSubmit = async (data) => {
    setisLoading(true);
    // Perform password change operation here
    setisLoading(false);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      {/* Form fields for current password, new password, and confirm password */}
    </form>
  );
};

export default ChangePassword;
```

- **Component**: `ChangePassword`
- **Hooks**: Uses `useState` and `useForm` for state and form handling.
- **Validation**: Utilizes Yup for form validation.
- **Features**: Password strength bar and toggle visibility for passwords.

---

## EditGameName.jsx

### 📄 Overview

- **Purpose**: Allows users to edit their game account names.
- **Features**: Form validation and asynchronous update of game tag.

### 💻 Code Explanation

```javascript
import React, { useState } from "react";
import { useForm } from "react-hook-form";
import * as Yup from "yup";

const EditGameName = (props) => {
  const [isLoading, setisLoading] = useState(false);

  const validationSchema = Yup.object().shape({
    gaming_account: Yup.string()
      .max(20, "Max 20 characters")
      .required("Account Username is required"),
  });

  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(validationSchema),
  });

  const onSubmit = async (data) => {
    setisLoading(true);
    // Call service to update gamer tag
    setisLoading(false);
  };

  return (
    <Form onSubmit={handleSubmit(onSubmit)}>
      {/* Form fields for editing game names */}
    </Form>
  );
};

export default EditGameName;
```

- **Component**: `EditGameName`
- **Features**: Displays a form for editing game account names.
- **Validation**: Ensures that the game account name is valid and within character limits.

---

## EditPicture.jsx

### 📄 Overview

- **Purpose**: Provides a UI for users to upload and edit their profile pictures using cropping tools.
- **Features**: Image upload, cropping, and saving to server.

### 💻 Code Explanation

```javascript
import React, { useState } from "react";
import ImageCropper from "../Image-clipper/ImageCropper";

const EditPicture = (props) => {
  const [imageToCrop, setImageToCrop] = useState(undefined);
  const [croppedImage, setCroppedImage] = useState(undefined);

  const onUploadFile = (event) => {
    if (event.target.files && event.target.files.length > 0) {
      const reader = new FileReader();
      reader.addEventListener("load", () => setImageToCrop(reader.result));
      reader.readAsDataURL(event.target.files[0]);
    }
  };

  const uploadAvatar = () => {
    // Call service to upload cropped image
  };

  return (
    <Modal>
      <input type="file" accept="image/*" onChange={onUploadFile} />
      <ImageCropper
        imageToCrop={imageToCrop}
        onImageCropped={(croppedImage) => {
          setCroppedImage(croppedImage);
        }}
      />
    </Modal>
  );
};

export default EditPicture;
```

- **Component**: `EditPicture`
- **Features**: Allows users to upload an image, crop it with a cropping tool, and save it as their avatar.
- **Functionality**: Uses the `ImageCropper` component for image manipulation.

---

## EditProfile.jsx

### 📄 Overview

- **Purpose**: Allows users to edit various details of their profiles.
- **Features**: Form validation, OTP verification for sensitive changes, manages age restrictions.

### 💻 Code Explanation

```javascript
import React, { useState, useEffect } from "react";
import { useForm } from "react-hook-form";
import * as Yup from "yup";

const EditProfile = (props) => {
  const [countries, setCountries] = useState([]);

  useEffect(() => {
    // Fetch countries for dropdown
  }, []);

  const validationSchema = Yup.object().shape({
    firstName: Yup.string().min(2).max(50).required(),
    lastName: Yup.string().min(2).max(50).required(),
    street: Yup.string().required(),
    city: Yup.string().required(),
    state: Yup.string().required(),
    postalCode: Yup.string().required(),
    country: Yup.string().required(),
    phoneNumber: Yup.number().required().positive().integer().min(8),
    discordId: Yup.string().nullable(),
  });

  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(validationSchema),
  });

  const onSubmit = async (data) => {
    // Handle profile update
  };

  return (
    <Form onSubmit={handleSubmit(onSubmit)}>
      {/* Form fields for profile information */}
    </Form>
  );
};

export default EditProfile;
```

- **Component**: `EditProfile`
- **Features**: 
  - Validates user input for various profile fields.
  - Handles OTP verification for phone number changes.
  - Provides country selection and validation.

---

## GameAccount.jsx

### 📄 Overview

- **Purpose**: Manages the addition of new game accounts.
- **Features**: Form to add new game accounts with validation.

### 💻 Code Explanation

```javascript
import React, { useState, useEffect } from "react";
import { useForm } from "react-hook-form";
import * as Yup from "yup";

const GameAccount = (props) => {
  const [games, setgames] = useState([]);

  useEffect(() => {
    // Fetch available games
  }, []);

  const validationSchema = Yup.object().shape({
    game_id: Yup.number().min(1).required(),
    gaming_account: Yup.string().max(20).required(),
  });

  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(validationSchema),
  });

  const onSubmit = async (data) => {
    // Handle the addition of new game account
  };

  return (
    <Form onSubmit={handleSubmit(onSubmit)}>
      {/* Form fields to add game accounts */}
    </Form>
  );
};

export default GameAccount;
```

- **Component**: `GameAccount`
- **Features**: 
  - Provides a list of games for the user to select from.
  - Allows the user to add a new game account with validation.

---

## PaypalAccount.js

### 📄 Overview

- **Purpose**: Enables users to add or update their PayPal account information.
- **Features**: Email validation and submission to backend.

### 💻 Code Explanation

```javascript
import React, { useState } from "react";
import { useForm } from "react-hook-form";
import * as Yup from "yup";

const PaypalAccount = (props) => {
  const [isLoading, setisLoading] = useState(false);

  const validationSchema = Yup.object().shape({
    paypalId: Yup.string().email().required(),
  });

  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(validationSchema),
  });

  const onSubmit = async (data) => {
    // Handle PayPal ID submission
  };

  return (
    <Form onSubmit={handleSubmit(onSubmit)}>
      {/* Form field for PayPal ID */}
    </Form>
  );
};

export default PaypalAccount;
```

- **Component**: `PaypalAccount`
- **Features**: 
  - Validates the PayPal ID as an email.
  - Allows users to add or update their PayPal ID for transactions.

---

## MyProfile.jsx

### 📄 Overview

- **Purpose**: Displays the user’s profile and allows various interactions such as editing profile details, managing game accounts, and social media connections.
- **Features**: Profile completion progress, editable profile information, social media integration.

### 💻 Code Explanation

```javascript
import React, { Component } from "react";

class MyProfile extends Component {
  constructor(props) {
    super(props);
    this.state = {
      showEditModal: false,
      userData: null,
    };
  }

  componentDidMount() {
    this.fetchUserData();
  }

  fetchUserData() {
    // Fetch user details from the server
  }

  showEditMod() {
    this.setState({ showEditModal: true });
  }

  hideEditMod() {
    this.setState({ showEditModal: false });
  }

  render() {
    return (
      <div>
        {/* Display User Profile with options to edit and manage accounts */}
      </div>
    );
  }
}

export default withRouter(MyProfile);
```

- **Component**: `MyProfile`
- **Features**: 
  - Displays the user’s full profile.
  - Provides options to edit profile details and manage connected accounts.
  - Displays profile completion status and integrates with other components for editing.

---

## PlayerProfile.jsx

### 📄 Overview

- **Purpose**: Provides a detailed view of another player's profile, allowing interactions such as sending friend requests.
- **Features**: Friend request handling, profile masking.

### 💻 Code Explanation

```javascript
import React, { useEffect, useState } from "react";

const PlayerProfile = (props) => {
  const [playerProfileDetail, setPlayerProfile] = useState(null);

  useEffect(() => {
    // Fetch player profile details
  }, []);

  const handleFriend = async (id) => {
    // Handle sending friend request
  };

  return (
    <div>
      {/* Display other player's profile with interaction options */}
    </div>
  );
};

export default withRouter(PlayerProfile);
```

- **Component**: `PlayerProfile`
- **Features**: 
  - Displays detailed information of another player's profile.
  - Allows sending of friend requests and displays friendship status.
  
---

Each of these components plays an integral role in creating a cohesive user profile management system. They leverage modern React approaches for managing state, handling forms, and interacting with backend services.