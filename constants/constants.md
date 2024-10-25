# 📚 Code Documentation

Welcome to the comprehensive documentation for the JavaScript files: `LobbyType.constant.js`, `LobbyCurrrentStatusConstant.js`, and `paymentConstantTypes.js`. This documentation provides detailed information about the purpose and functionality of each file. Let's dive in! 🚀

## 📜 Index

1. [LobbyType.constant.js](#lobbytypeconstantjs)
2. [LobbyCurrrentStatusConstant.js](#lobbycurrrentstatusconstantjs)
3. [paymentConstantTypes.js](#paymentconstanttypesjs)

---

## 1. `LobbyType.constant.js`

### Overview

This file defines constants that represent different types of lobbies within an application. The constants are used to differentiate between the current and previous lobbies.

### Code Explanation

```javascript
export default {
    CURRENT_LOBBIES: "current",
    PREVIOUS_LOBBIES: "previous",
};
```

### Breakdown

- **Purpose**: To provide string constants for identifying the type of lobby.
- **Constants**:
  - **CURRENT_LOBBIES**: Represents the current active lobbies.
  - **PREVIOUS_LOBBIES**: Represents the lobbies that have been completed or are no longer active.

### Usage

These constants are likely used in the application wherever there is a need to categorize or filter lobbies based on their status as current or previous.

---

## 2. `LobbyCurrrentStatusConstant.js`

### Overview

This file provides constants that define the current status of a lobby. These statuses help track the lifecycle of a lobby from its creation to its completion.

### Code Explanation

```javascript
const LobbyCurrentStatus = {
    UPCOMING: 1,
    ACTIVE: 2,
    ENDED: 3,
};

export default LobbyCurrentStatus;
```

### Breakdown

- **Purpose**: To define numeric constants for different stages of a lobby's lifecycle.
- **Constants**:
  - **UPCOMING**: Denoted by `1`, indicating a lobby that is scheduled to start.
  - **ACTIVE**: Denoted by `2`, indicating a lobby that is currently ongoing.
  - **ENDED**: Denoted by `3`, indicating a lobby that has concluded.

### Usage

These constants are used to manage and query the status of lobbies across the application, allowing for logic to be applied based on whether a lobby is upcoming, active, or ended.

---

## 3. `paymentConstantTypes.js`

### Overview

This file defines an array of objects, each representing a specific type of payment-related action or status. These constants are crucial for handling various payment scenarios within the application.

### Code Explanation

```javascript
const PaymentConstantTypes = [
    { label: "ADD TO WALLET", value: 1 },
    { label: "REDEEM BALANCE", value: 2 },
    { label: "PAY ENTRY FEE", value: 3 },
    { label: "RECEIVE WINNING", value: 4 },
    { label: "WINNINGS SEIZED", value: 5 },
    { label: "WALLET BALANCE SEIZED", value: 6 },
    { label: "REFUND", value: 7 },
    { label: "ON HOLD", value: 8 },
    { label: "RECEIVE REFERRAL", value: 9 },
    { label: "RECEIVE BONUS", value: 10 },
];

export default PaymentConstantTypes;
```

### Breakdown

- **Purpose**: To provide a comprehensive list of payment-related actions and statuses for transaction management.
- **Objects**:
  - **ADD TO WALLET**: Action to add funds to a user's wallet.
  - **REDEEM BALANCE**: Action where a user withdraws funds from their balance.
  - **PAY ENTRY FEE**: Payment for entering a competition or event.
  - **RECEIVE WINNING**: Crediting winnings to a user's account.
  - **WINNINGS SEIZED**: Status where winnings are withheld.
  - **WALLET BALANCE SEIZED**: Status where wallet funds are frozen.
  - **REFUND**: Returning money to a user.
  - **ON HOLD**: Status indicating a pending or paused transaction.
  - **RECEIVE REFERRAL**: Credit for bringing new users to the platform.
  - **RECEIVE BONUS**: Bonus funds awarded to a user.

### Usage

These constants are essential for maintaining clarity and consistency when handling payments, providing a standardized way to reference different types of payment actions within the application.

---

## Conclusion

Each of these files plays a crucial role in the application's architecture:
- **`LobbyType.constant.js`** helps categorize lobbies.
- **`LobbyCurrrentStatusConstant.js`** tracks the lifecycle status of lobbies.
- **`paymentConstantTypes.js`** manages payment-related actions and statuses.

Together, these constants ensure that the application runs smoothly and efficiently, providing a clear framework for handling lobbies and payments. 💼✨