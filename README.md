# CodeSync - Real-time Collaborative System

A complete, working real-time collaborative system with Node.js backend and React frontend.

## Features

- ✅ Real-time user presence tracking
- ✅ WebSocket communication via Socket.io
- ✅ Multi-room support
- ✅ Zero mock data - all data from live socket events
- ✅ Beautiful, responsive UI
- ✅ Connection status indicator

## Project Structure

```
codesync-v2/
├── server/              # Node.js + Express + Socket.io backend
│   ├── package.json
│   └── server.js        # Main server file
├── frontend/            # React + Vite frontend (NEW UI)
│   ├── src/
│   │   ├── App.jsx                    # Main app with routing
│   │   ├── main.jsx                   # React root
│   │   ├── components/
│   │   │   ├── Editor.jsx
│   │   │   ├── ChatPanel.jsx
│   │   │   ├── OutputConsole.jsx
│   │   │   ├── ProblemPanel.jsx
│   │   │   └── ...
│   │   ├── hooks/
│   │   │   └── useSocket.js           # Socket.io hook
│   │   ├── pages/
│   │   │   ├── LandingPage.jsx
│   │   │   └── RoomPage.jsx
│   │   ├── state/
│   │   │   ├── RoomContext.jsx
│   │   │   └── roomState.js
│   │   └── styles/
│   │       └── global.css
│   ├── vite.config.js
│   ├── package.json
│   └── index.html
└── README.md
```

## Quick Start

### Prerequisites

- Node.js 16+ and npm

### Installation & Running

#### Terminal 1: Start the Server

```bash
cd server
npm install
npm start
```

Server will run on http://localhost:5000

#### Terminal 2: Start the Frontend

```bash
cd frontend
npm install
npm run dev
```

Frontend will run on http://localhost:5173

### Usage

1. Open http://localhost:5173 in your browser
2. Enter a room ID (e.g., "room-1")
3. Click "Join Room"
4. Open another tab with the same room ID to see real-time user updates
5. Watch users appear/disappear in real-time as you open/close tabs

## How It Works

### Backend (server.js)

- **Connection Handler**: Logs when users connect
- **room:join Event**: 
  - User joins a room
  - Socket joins the room namespace
  - User is added to room's user list
  - All users in room receive updated user list
- **Disconnect Event**:
  - User is removed from room
  - Remaining users receive updated user list

### Frontend

- **useSocket Hook**: Manages Socket.io connection to backend
- **App.jsx**: Room ID input and navigation
- **RoomPage.jsx**:
  - Gets room ID from URL
  - Creates unique user ID on mount
  - Emits room:join event
  - Listens for room:users events
  - Displays live user count and list
  - Shows connection status

## Key Features Implemented

✅ Real-time presence (no polling)
✅ Multi-room isolation
✅ User UUID generation
✅ Proper cleanup on disconnect
✅ Connection status indicator
✅ Responsive UI
✅ No mock/default data
✅ Auto-reconnection support

## Testing

Open multiple browser tabs with the same room ID and verify:
- Users count increases when new tabs join
- Users count decreases when tabs close
- User names appear immediately
- Connection status updates in real-time

## Technologies

**Backend:**
- Express.js - HTTP server
- Socket.io - Real-time communication
- CORS - Cross-origin requests
- Node.js - JavaScript runtime

**Frontend:**
- React - UI library
- Vite - Build tool
- React Router - Page navigation
- Socket.io Client - WebSocket client
- CSS3 - Styling with animations

## Performance

- Lightweight socket events
- Efficient room management
- No unnecessary re-renders
- Cleanup on unmount
- Auto-reconnection

## Error Handling

- Socket connection errors logged to console
- Reconnection attempts with exponential backoff
- UI updates reflect connection state
- Graceful handling of network failures

---

Built with ❤️ for real-time collaboration
