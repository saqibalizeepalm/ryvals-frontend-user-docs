# 📸 ImageCropper Component Documentation

Welcome to the **ImageCropper** component documentation! This document serves as a guide to understanding how the ImageCropper component works, what it does, and how it can be utilized in your React applications. Let's dive in! 🏊‍♂️

## 🌈 Table of Contents

1. [Overview](#overview)
2. [Installation](#installation)
3. [Component Breakdown](#component-breakdown)
4. [Props](#props)
5. [Functions and Methods](#functions-and-methods)
6. [How It Works](#how-it-works)
7. [Dependencies](#dependencies)
8. [Conclusion](#conclusion)

## 🌟 Overview

The **ImageCropper** component is a React component that allows users to crop images directly in the browser. It leverages the `react-image-crop` library to provide a user-friendly interface for selecting and cropping parts of an image. Once cropped, the image can be uploaded to Azure Blob Storage.

## ⚙️ Installation

To use the ImageCropper component in your project, ensure you have the required dependencies:

```bash
npm install react react-dom react-image-crop
```

You will also need to ensure you have the necessary Azure services set up for token retrieval and file upload.

## 🧩 Component Breakdown

Here's a detailed breakdown of the component and its primary features:

| Component Part | Description |
|----------------|-------------|
| **State Management** | Utilizes React's `useState` and `useEffect` hooks to manage state, including Azure tokens and cropped image data. |
| **Image Cropping** | Uses the `ReactCrop` component for selecting and previewing the crop area. |
| **Azure Integration** | Integrates with Azure Blob Storage for uploading the cropped image. |

## 📬 Props

The component accepts the following props:

- **`imageToCrop`**: The source image that you want to crop.
- **`onImageCropped`**: A callback function that is called once the image is cropped, providing the cropped image data.

Usage example:

```jsx
<ImageCropper 
    imageToCrop="path/to/image.jpg"
    onImageCropped={(croppedImage) => console.log(croppedImage)}
/>
```

## 🛠️ Functions and Methods

### 1. **makeid**

Generates a random string of a specified length. Used to create unique filenames for cropped images.

```jsx
function makeid(length) {
    var result = "";
    var characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
    var charactersLength = characters.length;
    for (var i = 0; i < length; i++) {
        result += characters.charAt(Math.floor(Math.random() * charactersLength));
    }
    return result;
}
```

### 2. **cropImage**

Handles the image cropping process, including calling `getCroppedImage` and managing the crop configuration.

### 3. **getCroppedImage**

Creates a cropped image from the source image. It uses a canvas to draw the cropped portion and then converts it to a Blob for further processing.

### 4. **setcroppedImageLink**

Saves the uploaded image link to local storage.

## 🧠 How It Works

1. **Initialize State**: The component initializes its state to store Azure tokens, URLs, cropping configuration, and image references.
   
2. **Get Azure Token**: On component mount, it fetches an Azure token needed for uploading the image.
   
3. **Image Cropping**: The user selects a crop area on the image using the `ReactCrop` component. The crop configuration is updated accordingly.

4. **Image Processing**: The cropped area is drawn on a canvas, converted to a Blob, and then uploaded to Azure Blob Storage.

5. **Output**: Once uploaded, the cropped image link is stored locally, and a callback function is called to handle the final image.

## 📦 Dependencies

- **React**: For building the component.
- **React Image Crop**: Provides the cropping functionality.
- **Azure Services**: For uploading images.

## 📚 Conclusion

The **ImageCropper** component is a powerful and flexible tool for image manipulation in React applications. With its seamless integration to Azure services and user-friendly interface, it simplifies the process of cropping and uploading images.

We hope this documentation helps you understand and utilize the ImageCropper component effectively. Happy cropping! 🎉

Feel free to reach out if you have any questions or need further assistance.