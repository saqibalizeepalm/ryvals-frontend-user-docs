# Project Documentation

Welcome to the comprehensive documentation for the project components. Below is an extensive guide to understanding each component, their purpose, and how they integrate to form the overall application.

## Index

1. [ComplaintForm.jsx](#complaintformjsx)
2. [AddTeamMate.jsx](#addteammatejsx)
3. [CountDown2.jsx](#countdown2jsx)
4. [CountDown.jsx](#countdownjsx)
5. [CountDownStopEnrollment.jsx](#countdownstopenrollmentjsx)
6. [dummyData.js](#dummydatajs)
7. [EnrollButton.jsx](#enrollbuttonjsx)
8. [EnrollTeam.jsx](#enrollteamjsx)
9. [LobbyCard.jsx](#lobbycardjsx)
10. [GuLagInfo.jsx](#gulaginfojsx)
11. [LobbyDetail.jsx](#lobbydetailjsx)
12. [LobbyList.jsx](#lobbylistjsx)
13. [Participants.jsx](#participantsjsx)
14. [ParticipantItem.jsx](#participantitemjsx)
15. [PlayerStats.jsx](#playerstatsjsx)
16. [RegisterTeam.jsx](#registerteamjsx)

---

### ComplaintForm.jsx

**Purpose**: This component provides a form for users to file a complaint against an opponent within a game lobby. It includes validation and submission logic.

**Features**:
- 📝 Form validation using Yup and React Hook Form.
- 📃 Displays lobby details such as game name, date, and times.
- 👥 Allows users to select an opponent and provide complaint details.

**Code Snippet**:
```jsx
const validationSchema = Yup.object().shape({
  username: Yup.string().required("Opponent game id is required"),
  link: Yup.string().matches(...).required("Link is required"),
  message: Yup.string().required("Message is required"),
});
```

---

### AddTeamMate.jsx

**Purpose**: Facilitates the addition of teammates to a game lobby.

**Features**:
- ✅ Supports filtering teammates based on lobby and team requirements.
- 🔄 Provides functionality to add or remove teammates.

**Code Snippet**:
```jsx
const addTeamMate = () => {
  setSelectedTeamMates((prev) => [...prev, teamMate]);
  setTeamMate(null);
};
```

---

### CountDown2.jsx

**Purpose**: Displays a countdown timer for a specific event using the `react-countdown` library.

**Features**:
- ⏰ Converts server time to UTC and calculates countdown end time.
- 📅 Renders a formatted countdown display.

**Code Snippet**:
```jsx
const countdownTimer = ({ days, hours, minutes, seconds, completed }) => {
  if (completed) {
    return "";
  } else {
    return (
      <span>Starts in {days}D {hours}H {minutes}M {seconds}S</span>
    );
  }
};
```

---

### CountDown.jsx

**Purpose**: Similar to `CountDown2.jsx`, but specifically handles a different countdown event.

**Features**:
- 🕒 Countdown logic with completion handling.
- 📡 Uses `dateToUtc` for time conversion.

**Code Snippet**:
```jsx
<Countdown date={currentTimeStamp} date={endTime} renderer={countdownTimer} />
```

---

### CountDownStopEnrollment.jsx

**Purpose**: Manages a countdown that signals when enrollment for a lobby will stop.

**Features**:
- 🕒 Subtracts a specific time frame from the current time to calculate the end time.
- 📅 Integrates a completion callback to handle the end of the countdown.

**Code Snippet**:
```jsx
const subtractDate = new Date(currentDate.getTime() - minutesToSubtract * 60000);
```

---

### dummyData.js

**Purpose**: Provides static data including color options and teammate information for use throughout the application.

**Features**:
- 🎨 Color options with hex codes.
- 👥 Mock data for selected teammates and teams.

**Code Snippet**:
```javascript
export const selectedTeamMates = [{ username: "temp" }, { username: "temp" }];
export const TEAMS = ["Alpha", "SOUL", "RDX"];
```

---

### EnrollButton.jsx

**Purpose**: Allows users to enroll in a game lobby, handling payment and verification requirements.

**Features**:
- 💰 Manages wallet balance and promo options.
- 🔄 Handles multiple enrollment statuses and user interactions.

**Code Snippet**:
```jsx
const checkBalance = () => {
  getWalletBalance().then((res) => {
    setwalletBalance(res.wallet_balance);
  });
};
```

---

### EnrollTeam.jsx

**Purpose**: Manages the process of enrolling a team into a lobby, including team registration and payment.

**Features**:
- 👥 Integrates teammate selection with registration.
- 💸 Offers a payment interface for team enrollment.

**Code Snippet**:
```jsx
const handleRegister = () => {
  if (canRegisterTeamName && selectedTeamMates.length >= props?.mode - 1) {
    setEnrollTeamStep(1);
  }
};
```

---

### LobbyCard.jsx

**Purpose**: Displays detailed information about a game lobby, including status, rewards, and enrollment options.

**Features**:
- 🏆 Shows lobby status and entry fees.
- ⏱ Integrates countdown components to display start times.

**Code Snippet**:
```jsx
<EnrollButton {...this.props} isTimeCompleted={this.state.isTimerReached} stop={this.state.isTimerReached3} />
```

---

### GuLagInfo.jsx

**Purpose**: Provides additional information regarding rules and requirements for participating in a game lobby.

**Features**:
- 🚫 Details on respawn rules and Discord requirements.
- 📢 Modal display for information dissemination.

**Code Snippet**:
```jsx
<p class="respawn-text">Players MAY NOT RESPAWN teammates...</p>
```

---

### LobbyDetail.jsx

**Purpose**: Offers an in-depth view of a specific game lobby, with options to file complaints, view participants, and check stats.

**Features**:
- 📄 Displays detailed lobby information and rules.
- 📝 Complaint form integration for reporting issues.

**Code Snippet**:
```jsx
<ComplaintForm {...this.state.lobbyData} game_slug={this.game_slug} onComplete={() => this.handleModal()} />
```

---

### LobbyList.jsx

**Purpose**: Lists all available game lobbies with filtering and pagination options.

**Features**:
- 🔍 Filters lobbies by type, amount, and mode.
- 📃 Pagination support for navigating large lists.

**Code Snippet**:
```jsx
<Form.Select className="dropdown-dropper" onChange={(ev) => onLobbyFilterChange(ev)}>
  <option value={LobbyTypeConstant.CURRENT_LOBBIES}>Current lobbies</option>
</Form.Select>
```

---

### Participants.jsx

**Purpose**: Displays participants of a lobby and their registration status.

**Features**:
- 👥 Shows team and player details.
- ✔️ Owner identification for team management.

**Code Snippet**:
```jsx
<div className="participantsBox">
  <ParticipantItem user={user} participantData={props?.participantData} owner={owner} {...props} />
</div>
```

---

### ParticipantItem.jsx

**Purpose**: Manages individual participant details within a lobby, including invitation acceptance and replacement.

**Features**:
- 🔄 Allows team replacement and invitation management.
- 👥 Displays participant information and actions.

**Code Snippet**:
```jsx
<Button className="declineAction acceptAction" onClick={() => setShowReplaceModal(true)}>Replace</Button>
```

---

### PlayerStats.jsx

**Purpose**: Displays player statistics for a game lobby, sorted by performance metrics.

**Features**:
- 📊 Shows data such as kills, assists, and winnings.
- 🏆 Sorted leaderboard presentation.

**Code Snippet**:
```jsx
<table style={{ color: "white" }}>
  <tr><th>Team number</th><th>Player name</th><th>Kills</th></tr>
</table>
```

---

### RegisterTeam.jsx

**Purpose**: Handles the registration of pre-made teams into a lobby.

**Features**:
- 🏷 Validates team name length and uniqueness.
- 🔄 Provides team selection options from pre-existing data.

**Code Snippet**:
```jsx
<Select placeholder="Team Name" isSearchable isClearable onInputChange={(value, action) => setInput(value)}>
</Select>
```

---

This documentation provides an overview of the components, highlighting their purpose and key features. Each component plays a crucial role in the functionality of the application, collaborating to provide a seamless user experience. If you have further questions or require more detailed explanations, please refer to the individual component files or reach out to the development team.