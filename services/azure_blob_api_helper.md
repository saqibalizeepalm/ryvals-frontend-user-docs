# 📄 Azure Blob API Helper Documentation

## Overview 📚

The `azure_blob_api_helper.js` file is a JavaScript module designed to interact with Azure Blob Storage. It provides functions to upload files to an Azure Blob container and generate accessible URLs for those files. This utility is particularly useful for web applications that need to handle file uploads and store them in the cloud.

---

## **Table of Contents** 📑

1. [Environment Variables](#environment-variables)
2. [Functions](#functions)
   - [createBlobInContainer](#createblobincontainer)
   - [getImageUrl](#getimageurl)
   - [uploadFileToBlob](#uploadfiletoblob)
3. [Usage Example](#usage-example)
4. [Conclusion](#conclusion)

---

## **Environment Variables** 🌍

This module relies on several environment variables to function properly. These must be configured in your environment, typically within a `.env` file:

- **`REACT_APP_AZURE_SAS_TOKEN`**: The Shared Access Signature (SAS) token for Azure Blob Storage.
- **`REACT_APP_AZURE_CONTAINER_NAME`**: The name of the container in Azure Blob Storage where files will be uploaded.
- **`REACT_APP_AZURE_STORAGE_NAME`**: The name of the Azure storage account.

These environment variables are crucial for authenticating and interacting with your Azure Blob Storage account.

---

## **Functions** 🔧

### `createBlobInContainer` 📥

```javascript
const createBlobInContainer = async (containerClient, file) => {
    // create blobClient for container
    const blobClient = containerClient.getBlockBlobClient(file.name);

    // set mimetype as determined from browser with file upload control
    const options = { blobHTTPHeaders: { blobContentType: file.type } };

    // upload file
    await blobClient.uploadBrowserData(file, options);
};
```

- **Purpose**: Uploads a file to a specified Azure Blob Storage container.
- **Parameters**:
  - `containerClient`: An instance of the container client, representing the Azure Blob container.
  - `file`: The file object to be uploaded.
- **Functionality**: 
  - Creates a blob client for the specified container.
  - Sets the MIME type for the file.
  - Uploads the file using the `uploadBrowserData` method.

### `getImageUrl` 🌐

```javascript
const getImageUrl = (fileName) => {
    return `https://${storageAccountName}.blob.core.windows.net/${containerName}/${fileName}`;
};
```

- **Purpose**: Generates a URL for accessing the uploaded file.
- **Parameters**:
  - `fileName`: The name of the file.
- **Returns**: A string URL pointing to the file location in Azure Blob Storage.

### `uploadFileToBlob` 🚀

```javascript
const uploadFileToBlob = async (file, azureToken, azureUrl) => {
    if (!file) return null;

    const blobService = new BlobServiceClient(azureUrl);
    const containerClient = blobService.getContainerClient(containerName);

    try {
        await createBlobInContainer(containerClient, file);
        return getImageUrl(file.name);
    } catch (error) {
        return null;
    }
};
```

- **Purpose**: The main function to handle the file upload process to Azure Blob Storage.
- **Parameters**:
  - `file`: The file object to be uploaded.
  - `azureToken`: The token needed for accessing Azure services (not used explicitly in the code).
  - `azureUrl`: The complete URL for accessing the Azure Blob service.
- **Returns**: The URL of the uploaded file or `null` if the upload fails.
- **Functionality**:
  - Instantiates a `BlobServiceClient` using the provided Azure URL.
  - Acquires a container client for the specified container.
  - Attempts to upload the file using `createBlobInContainer`.
  - Returns the file URL if successful; otherwise, returns `null`.

---

## **Usage Example** 📋

```javascript
import uploadFileToBlob from './azure_blob_api_helper';

// Example usage for uploading a file
const fileInput = document.querySelector('#file-input');
fileInput.addEventListener('change', async (event) => {
    const file = event.target.files[0];
    const azureUrl = `https://${storageAccountName}.blob.core.windows.net/?${sasToken}`;
    const fileUrl = await uploadFileToBlob(file, sasToken, azureUrl);

    if (fileUrl) {
        console.log('File successfully uploaded:', fileUrl);
    } else {
        console.error('Failed to upload file.');
    }
});
```

---

## **Conclusion** 🏁

The `azure_blob_api_helper.js` module provides an efficient way to upload files to Azure Blob Storage and retrieve their URLs for access. By leveraging Azure's Blob Service Client, this module abstracts the complexity of file uploads and offers an easy-to-use interface for developers.

Remember to configure the necessary environment variables and ensure your Azure Storage account is properly set up to use this utility effectively. Happy coding! 🚀