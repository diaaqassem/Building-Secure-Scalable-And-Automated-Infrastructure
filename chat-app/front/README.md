# Chat Application Frontend - ReactJS

This is the frontend implementation of a real-time chat application built with **ReactJS** and **Socket.IO**. The application allows users to create and join chat rooms, send and receive messages, and manage room membership dynamically. It also integrates user authentication with login and sign-up features.

---

## Features

1. **User Authentication**: 
   - Login and Signup functionality.
   - User data management using state.
   
2. **Chat Rooms**:
   - Create chat rooms with unique names.
   - Join or leave existing chat rooms using room IDs.

3. **Real-time Messaging**:
   - Send and receive messages instantly in chat rooms.
   - View message history in the room.

4. **Socket.IO Integration**:
   - Communicate with the backend server over WebSockets for real-time updates.

5. **Dynamic Routing**:
   - Routes for login, signup, and the chat interface.

6. **Frontend Styling**:
   - Fully styled UI using CSS for an engaging user experience.

---

## Installation and Setup

### Prerequisites:
- **Node.js** installed on your system.
- A backend server for WebSocket communication (Refer to the backend repository).

### Steps to Run:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/diaaqassem/Chat-Application-Frontend---ReactJS.git
   cd Chat-Application-Frontend---ReactJS
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run the Development Server**:
   ```bash
   npm run start
   ```
   - The app will run on `http://localhost:3000`.

---

## Usage

### Login/Signup:
- Navigate to the `/login` route to log in using existing credentials or to the `/signup` route to create a new account.

### Chat Functionalities:
1. **User Identification**:
   - Enter your unique user ID in the input field.

2. **Room Management**:
   - Create a room: Provide a unique room name and click "Create Room".
   - Join a room: Enter the room ID to join and click "Join Room".
   - Leave a room: Provide the room ID and click "Leave Room".

3. **Messaging**:
   - Type your message in the message input field and click "Send" to broadcast it to the room.

---

## File Structure

```
src/
├
│─ ChatApp.js      # Main chat application component
├─ Login.js        # Login functionality
├─ SignUp.js       # Sign-up functionality
├── App.js              # Entry point for routes
├── index.css           # Styles for the application
├── index.js            # Application bootstrap
```

---

## Key Technologies

- **ReactJS**: Frontend framework for UI components and state management.
- **Socket.IO**: Real-time, bidirectional communication.
- **React Router**: For navigating between login, signup, and chat interfaces.
- **CSS**: Styling the user interface.

---

## Example Screenshots
![image](https://github.com/user-attachments/assets/b0d4fff1-9a76-4695-8988-7aa28ef26347)
![image](https://github.com/user-attachments/assets/9af47a7c-c03b-4e3c-bada-ef34fb096ea9)

![image](https://github.com/user-attachments/assets/271013c3-3a00-45a4-85bd-98964267752c)

### Login Page
- A user-friendly login interface.

### Chat Interface
- A real-time chat room with message history and dynamic updates.

---

## Environment Variables

Configure the server URL in the `socket` initialization within `ChatApp.js`:
```javascript
const socket = io("http://localhost:5001", {
  transports: ["websocket"],
  cors: {
    origin: "http://localhost:3000",
    methods: ["GET", "POST"],
  },
});
```

---
