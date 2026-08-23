# FSE Chat Room

FSE Chat Room is a simple real-time web chat application built for the Foundations of Software Engineering preparation assignment.



## PROJECT PURPOSE

The goal of this project is to practice building a full-stack web application using a required technology stack, including a vanilla JavaScript frontend, an Express.js backend, database persistence, JWT-based authentication, and Socket.IO for real-time updates.

The application allows users to:

* Register a new account with a username and password.
* Log in securely using JWT authentication.
* View previous chat messages stored in the database.
* Send new chat messages.
* See new messages from other users instantly without refreshing the page.
* Log out safely from the chat room.

All user information and chat messages are stored persistently in the database, so users can leave and re-enter the application without losing previous data.

The application is designed to run locally on `localhost` and supports Chrome browser usage with a mobile-responsive layout.



# TECHNOLOGIES USED

## Client Side

### HTML

HTML is used to create the structure of the application's pages, including:

* Login page
* Registration page
* Chat room page

The UI structure follows the provided FSE Chat Room mockup.

---

### CSS

CSS is used to control the layout, colors, fonts, spacing, and responsive design.

It is responsible for:

* Mobile-friendly page layout
* Chat message styling
* Header and button appearance
* Login and registration form styling

No external CSS frameworks or UI libraries are used.

---

### JavaScript

Vanilla JavaScript is used for all client-side logic.

It handles:

* User login and registration requests
* JWT token storage
* Sending chat messages through HTTP requests
* Loading previous messages
* Updating the UI dynamically
* Receiving real-time messages through Socket.IO

No frontend frameworks such as React, Vue, or Angular are used.


# Server Side

## Node.js

Node.js provides the runtime environment for the backend application. It handles HTTP requests, API routing, database operations, authentication logic and Socket.IO communication

## Express.js

Express.js is used as the backend web framework. It provides REST API endpoints, middleware support static file serving, and request handling.

The backend follows the required Express.js architecture.

## MongoDB Atlas

MongoDB Atlas is used as the database system. The database stores:

### Users
User documents contain username and password hash

### Messages
Message documents contain sender username, message content and timestamp.

MongoDB Atlas was selected as a cloud-based database because it provides persistent storage while allowing the application to run locally.

---

## Mongoose

Mongoose is used as the MongoDB object modeling library. It provides database connection management, schema definition and CRUD operations for users and messages.


## JSON Web Token (JWT)

JWT is used for authentication and authorization. The application uses JWT to authenticate users after login, protect chat-related API endpoints and verify that only logged-in users can access protected resources

The project implements JWT directly using a JWT library without using authentication frameworks such as Passport.js.


## Socket.IO

Socket.IO is used for real-time server-to-client communication. It is responsible for broadcasting newly created messages and updating all connected users immediately.

Following the assignment requirement:

* Client-to-server communication uses HTTP requests.
* Server-to-client communication uses Socket.IO.

The client does not use Socket.IO to send messages.



# CODE ORGANIZATION

The project is organized into two main folders:

```
FSE-Chat-Room
│
├── client
│   ├── css
│   │   └── styles.css
│   │
│   ├── pages
│   │   ├── chat.html
│   │   ├── index.html
│   │   └── register.html
│   │
│   └── scripts
│       ├── auth.js
│       ├── chat.js
│       └── register.js
│
├── server
│   ├── controllers
│   │   ├── auth.controller.js
│   │   └── chat.controller.js
│   │
│   ├── middleware/
│   │      auth.middleware.js
│   │
│   ├── models
│   │   ├── message.model.js
│   │   └── user.model.js
│   ├── routes/
│   │   ├── auth.routes.js
│   │   └── chat.routes.js
│   │
│   ├── socket/
│   │      socket.js
│   │
│   ├── app.js
│   └── db.js
│
├── .env
├── .gitignore
├── package.json
├── README.md
├── RESOURCES.md
└── MYPROMPTS.md
```


# Client Folder

The `client` folder contains all frontend code.

## css/

### styles.css

Contains all styling rules for:

* Login page
* Registration page
* Chat room
* Responsive mobile layout



## pages/

### index.html

The login page. Users can enter username and password, login into the chat room and navigate to registration.

### register.html

The registration page. Users can create a new account. After successful registration, users are redirected back to login.

### chat.html

The main chat room interface. It contains chat header, message display area, message input area and a logout button.



## scripts/

### login.js

All requests related with login. Handles login requests, JWT storage and redirecting users into the chat room.

### register.js

All requests related with registration. Handles new user registration, registration validation and redirecting users back to login.

### chat.js

All requests related with sending and viewing messages. Handles loading previous messages, sending new messages using HTTP POST requests, displaying messages, Socket.IO client connection and logout functionality.



# Server Folder

The `server` folder contains backend logic.

## app.js

The main entry point of the application. It creates the Express server, registers API routes, serves frontend files and initializes Socket.IO

## db.js
Handles MongoDB Atlas connection.


## models/

### user.model.js

Defines the user schema. Stores Username and Password information.

### message.model.js

Defines the chat message schema. Stores Username, Message text and Creation timestamp.


## controllers/

### chat.controller.js

Contains backend application logic. Responsible for registering users, logging users in, validating JWT tokens, saving messages, retrieving previous messages and broadcasting new messages.



# SET-UP INSTRUCTIONS

## 1. Install Dependencies

Clone the repository:

```bash
git clone <repository-url>
```

Navigate into the project folder:

```bash
cd FSE-Chat-Room
```

Install required packages:

```bash
npm install
```


## 2. Configure Environment Variables

Create a `.env` file in the project root directory.

Example:

```env
PORT=3000

MONGO_URI=mongodb+srv://<username>:<password>@<cluster-url>/fse-chat-room

JWT_SECRET=mySecretKey
```

Replace:

```
<username>
<password>
<cluster-url>
```

with your MongoDB Atlas credentials.


## 3. Start the Application

Run the development server:

```bash
npm run dev
```

The server will start on:

```
http://localhost:3000
```


## 4. Open the Application

Open Chrome and visit:

```
http://localhost:3000/pages/index.html
```


## 5. Testing Real-Time Updates

To test Socket.IO real-time functionality:

1. Open the application in a normal Chrome window.
2. Open the application again in an Incognito Chrome window.
3. Login with two different accounts.
4. Send messages from either window.
5. Confirm that both users receive new messages instantly without refreshing.


# Database Setup

This project uses MongoDB Atlas.

To use your own database:

1. Create a MongoDB Atlas cluster.
2. Create a database user.
3. Allow your IP address.
4. Copy the connection string.
5. Add it to `.env`:

```env
MONGO_URI=<your-mongodb-atlas-connection-string>
```


# LINK TO YOUTUBE VIDEO

The demonstration video is available here:

<https://youtu.be/BkOzRB_A7lc>


---
