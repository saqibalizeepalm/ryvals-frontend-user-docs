# 📚 Documentation

This documentation provides a detailed explanation of the JavaScript and React code files you provided. It includes an index for easy navigation.

## Index

- [authToken.js](#authtokenjs) 🌐
- [DateFormatter.js](#dateformatterjs) 🗓️
- [loggedInUser.js](#loggedinuserjs) 👤
- [LocalToUtc.js](#localtoutcjs) 🌍
- [utilities.js](#utilitiesjs) 🛠️
- [toastify.jsx](#toastifyjsx) 🍞
- [Paginator.jsx](#paginatorjsx) 📄

---

## authToken.js 🌐

### **Functionality**

The `authToken.js` file provides a function to retrieve an authentication token from the local storage. If the user is logged in and an access token is available, it returns the token in the "Bearer" format. If not, it returns `null`.

### **Code Explanation**

```javascript
export default function AuthToken() {
    const obj = JSON.parse(localStorage.getItem("user"));
    if (obj && obj.access_token) {
        return `Bearer ${obj.access_token}`;
    } else {
        return null;
    }
}
```

- **Local Storage**: Retrieves the user object stored under the "user" key.
- **Access Token**: Checks if the user object contains an `access_token`. 
- **Return Value**: Returns `Bearer <access_token>` if available; otherwise, returns `null`.

---

## DateFormatter.js 🗓️

### **Functionality**

This file contains functions to format dates and times using the `dateformat` library.

### **Code Explanation**

```javascript
import dateFormat from "dateformat";

function DateTimeFormat(dateTime) {
    return dateFormat(dateTime, "mmm dd, yyyy hh:MM TT Z");
}

function DateFormat(dateTime) {
    return dateFormat(dateTime, "mmm dd, yyyy");
}

function TimeFormat(dateTime) {
    return dateFormat(dateTime, "hh:MM TT Z");
}

export { DateTimeFormat, DateFormat, TimeFormat };
```

- **DateTimeFormat**: Formats a date and time string.
- **DateFormat**: Formats a date string.
- **TimeFormat**: Formats a time string.
- **Export**: Exports all three functions for external use.

---

## loggedInUser.js 👤

### **Functionality**

Determines if a user is currently logged in by checking the local storage for a user object.

### **Code Explanation**

```javascript
export default function LoggedInUser() {
    const obj = JSON.parse(localStorage.getItem("user"));
    return obj ? true : false;
}
```

- **Local Storage**: Retrieves the user object stored under the "user" key.
- **Return Value**: Returns `true` if a user object exists, otherwise `false`.

---

## LocalToUtc.js 🌍

### **Functionality**

Converts a given date to UTC format.

### **Code Explanation**

```javascript
function dateToUtc(datetime) {
    let date;
    if (typeof datetime === "string") date = new Date(datetime);
    else if (typeof datetime === "number") date = new Date(datetime);
    else date = datetime;
    
    return Date?.UTC(
        date?.getUTCFullYear(),
        date?.getUTCMonth(),
        date?.getUTCDate(),
        date?.getUTCHours(),
        date?.getUTCMinutes(),
        date?.getUTCSeconds()
    );
}

export default dateToUtc;
```

- **Date Conversion**: Converts the input to a `Date` object.
- **UTC Format**: Returns the date in UTC format using `Date.UTC`.

---

## utilities.js 🛠️

### **Functionality**

Contains various utility functions for date manipulation, mode enumeration, team mate filtering, and field masking.

### **Code Explanation**

```javascript
import moment from "moment";

export const isTodayorTommorrow = (date) => { /* ... */ };
export const dateStringTodayTommorrow = (date) => { /* ... */ };
export const modeEnum = { 1: "Solos", 2: "Duos", 3: "Trios", 4: "Quad" };
export const AddTeamMatefilterConfig = { /* ... */ };
export const convertTeamMatesToOptions = (arr = []) => { /* ... */ };
export const mask = (field) => { /* ... */ };
```

- **Date Functions**: Uses `moment` to determine if a date is today or yesterday and formats it accordingly.
- **Mode Enumeration**: Provides a mapping for game modes.
- **Team Mate Filtering**: Provides configuration for filtering teammates and converting them to a specific format.
- **Mask Function**: Masks a field by replacing characters with asterisks.

---

## toastify.jsx 🍞

### **Functionality**

Provides a function to display different types of toast notifications using `react-toastify`.

### **Code Explanation**

```javascript
import { toast } from "react-toastify";

const toastrOptions = {
    position: "top-right",
    autoClose: 5000,
    hideProgressBar: true,
    newestOnTop: false,
    closeOnClick: true,
    pauseOnHover: true,
    draggable: true,
    progress: undefined,
    pauseOnFocusLoss: false,
    theme: "colored",
};

function toastify(toastType, message) {
    switch (toastType) {
        case "info": toast.info(message, toastrOptions); break;
        case "warn": toast.warn(message, toastrOptions); break;
        case "warning": toast.warning(message, toastrOptions); break;
        case "error": toast.error(message, toastrOptions); break;
        case "success": toast.success(message, toastrOptions); break;
        default: toast(message, toastrOptions); break;
    }
}

export default toastify;
```

- **Toast Options**: Configures the appearance and behavior of the toast notifications.
- **Toast Types**: Displays different types of toasts ('info', 'warn', 'warning', 'error', 'success') based on the `toastType` parameter.

---

## Paginator.jsx 📄

### **Functionality**

A React component that provides pagination functionality using the `react-paginate` library.

### **Code Explanation**

```javascript
import React from "react";
import PropTypes from "prop-types";
import ReactPaginate from "react-paginate";

const Paginator = (props) => {
    const handlePageChange = ({ selected }) => {
        props.pageClick(selected + 1);
    };

    return (
        <>
            <div className="mt-3 page">
                {props.totalCount > props.pageSize ? (
                    <ReactPaginate
                        pageCount={props.totalCount / props.pageSize}
                        pageRangeDisplayed={3}
                        marginPagesDisplayed={1}
                        previousLabel={"<"}
                        nextLabel={">"}
                        breakLabel={"..."}
                        onPageChange={handlePageChange}
                        initialPage={0}
                        containerClassName={"pagination"}
                        pageClassName={"page-item"}
                        pageLinkClassName={"page-link"}
                        previousClassName={"page-item"}
                        previousLinkClassName={"page-link"}
                        nextClassName={"page-item"}
                        nextLinkClassName={"page-link"}
                        breakClassName={"page-link"}
                        breakLinkClassName={"page-item"}
                        activeClassName={"active"}
                        activeLinkClassName={"active"}
                        disabledClassName={"disabled"}
                    />
                ) : null}
            </div>
        </>
    );
};

Paginator.propTypes = {
    pageClick: PropTypes.func.isRequired,
    totalCount: PropTypes.number.isRequired,
    pageSize: PropTypes.number.isRequired,
};

export default Paginator;
```

- **Component**: Provides a pagination UI for navigating through pages.
- **Props**: Takes three props - `pageClick` (callback for page changes), `totalCount` (total item count), and `pageSize` (items per page).
- **ReactPaginate**: Renders pagination controls using the `react-paginate` library.

---

This documentation provides a comprehensive understanding of each file and its purpose, along with detailed code explanations. Feel free to explore each section for more insights!