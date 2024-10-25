# 📜 WalletTransaction.jsx Documentation

## 📄 Introduction

`WalletTransaction.jsx` is a React component designed to display a user's wallet transaction history. It provides a paginated view of transactions with details such as transaction ID, date, amount, wallet balance, and transaction type. The component makes use of several React hooks and custom services for data fetching.

---

## 📚 Table of Contents

1. [Imports and Dependencies](#imports-and-dependencies)
2. [Component Overview](#component-overview)
3. [State Variables](#state-variables)
4. [Effects and Data Fetching](#effects-and-data-fetching)
5. [Event Handlers](#event-handlers)
6. [Rendering Logic](#rendering-logic)
7. [Usage](#usage)
8. [Conclusion](#conclusion)

---

## 📥 Imports and Dependencies

The component relies on the following imports:

```javascript
import React, { useEffect, useState } from "react";
import Paginator from "../../helper/paginator/Paginator";
import { walletHistory } from "../../services/user.service";
import PaymentConstantTypes from "../../constants/paymentConstantTypes";
```

- **React, useState, useEffect**: Core React functionalities for creating components and handling state and side effects.
- **Paginator**: A custom pagination component.
- **walletHistory**: A service function to fetch wallet transaction data.
- **PaymentConstantTypes**: Constants that define various payment types.

---

## 🏗️ Component Overview

The `WalletTransaction` component is responsible for:

- Fetching and displaying a paginated list of wallet transactions.
- Allowing users to navigate through different pages of transactions.
- Categorizing transaction types and displaying them accordingly.

---

## 📊 State Variables

The component uses the following state variables:

| State Variable  | Type    | Description                                          |
|-----------------|---------|------------------------------------------------------|
| `transactions`  | Array   | Stores the list of transactions.                      |
| `totalCount`    | Number  | Total number of transactions available.               |
| `pageNum`       | Number  | Current page number in the pagination.                |

The **pageSize** and **pagination** variables are constants used for data fetching and UI rendering.

---

## ⏲️ Effects and Data Fetching

The component uses a `useEffect` to trigger data fetching whenever `pageNum` or `props.data` changes:

```javascript
useEffect(() => {
    getListing();
}, [pageNum, props.data]);

const getListing = async () => {
    let filter = { isPaginated: pagination, pageNum: pageNum, pageSize: pageSize };
    await walletHistory(filter).then((res) => {
        if (pagination) {
            settransactions(res.data);
            settotalCount(res.total);
        } else {
            settransactions(res);
            settotalCount(res.length);
        }
    });
};
```

- **getListing**: Fetches transaction data from the server using the `walletHistory` service, applying pagination filters.

---

## 🎯 Event Handlers

The component handles user interactions with the following function:

```javascript
const handlePageClick = (pageNum) => {
    setpageNum(pageNum);
};
```

- **handlePageClick**: Updates the `pageNum` state to reflect the user's page selection.

---

## 🖼️ Rendering Logic

The main rendering logic of the component:

```javascript
return (
    <>
        {totalCount ? (
            <>
                <table style={{ color: "white" }}>
                    <tr>
                        <th>Transaction Id</th>
                        <th>Date</th>
                        <th>Amount</th>
                        <th>Wallet Balance</th>
                        <th>Transaction type</th>
                    </tr>
                    {transactions && transactions.map((trans, idx) => {
                        const paymentConst = PaymentConstantTypes.map((type) => type);
                        const paymentConstFilter = paymentConst.filter((paymentType) => paymentType.value === trans.type);
                        
                        return (
                            <tr key={idx}>
                                <td><p>{trans.transaction_number}</p></td>
                                <td>{new Date(trans.transaction_date).toLocaleString("en-US", {
                                    day: "numeric",
                                    year: "numeric",
                                    month: "long",
                                    hour: "numeric",
                                    minute: "numeric",
                                    second: "numeric",
                                    hour12: false,
                                })}</td>
                                <td>
                                    {[1, 4, 7, 9, 10].includes(trans.type) && (<p style={{ color: "green" }}>+ ${trans.amount}</p>)}
                                    {[2, 3, 5, 6].includes(trans.type) && (<p style={{ color: "red" }}>- ${trans.amount}</p>)}
                                    {[8].includes(trans.type) && (<p style={{ color: "#ff9900" }}>${trans.amount}</p>)}
                                </td>
                                <td>${trans.current_wallet_balance}</td>
                                <td>{trans.status === 3 ? `${paymentConstFilter[0].label} (pending)` : trans.status === 4 ? "ON HOLD" : trans.status === 2 ? "FAILED" : trans.transaction_mode === 1 ? "PROMO BONUS" : `${paymentConstFilter[0].label}`}</td>
                            </tr>
                        );
                    })}
                </table>
                <div>
                    {pagination ? (<Paginator totalCount={totalCount} pageSize={pageSize} pageClick={handlePageClick} />) : null}
                </div>
            </>
        ) : (
            <h5 style={{ textAlign: "center", padding: "20px" }}>No transactions yet</h5>
        )}
    </>
);
```

- **Table**: Displays transaction details with appropriate styling for credited, debited, and on-hold amounts.
- **Paginator**: Facilitates navigation through paginated data.
- **Conditional Rendering**: Displays a message if no transactions are available.

---

## 🛠️ Usage

To use the `WalletTransaction` component, import it into your React application and render it within your desired component or page. Pass any necessary props required for the component to function correctly.

---

## ✨ Conclusion

The `WalletTransaction.jsx` component provides a robust solution for displaying user wallet transaction history in a paginated format. It efficiently fetches and presents data with clear categorization and user-friendly navigation, enhancing the user experience in applications that require transaction monitoring.