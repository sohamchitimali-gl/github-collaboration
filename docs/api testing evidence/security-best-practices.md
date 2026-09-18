Step 1: Understand the frontend structure

frontend/
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/
│   ├── context/
│   ├── utils/
│   ├── App.jsx
│   └── main.jsx


Step 2: Document the component tree

App
│
├── Header
├── Sidebar
│
├── ChatPage
│   ├── ChatWindow
│   ├── MessageList
│   ├── MessageInput
│   └── Feedback
│
└── Footer


Step 3: Document data flow


User enters message
        ↓
MessageInput
        ↓
Chat handler
        ↓
Chat API
        ↓
Backend
        ↓
Response
        ↓
Chat state updated
        ↓
MessageList displays response


Step 4: Document API integration

ChatPage
   ↓
services/chatApi.js
   ↓
POST /api/chat


- HTTP method
- Endpoint
- Request body
- Response
- Authentication
- Error handling

