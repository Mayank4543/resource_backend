# Notes API - Backend

A RESTful API backend for a full-featured note-taking application with text formatting capabilities, user authentication, and pagination.

## 📋 Overview

This Node.js backend application provides a complete API for managing notes, handling user authentication, and supporting text formatting features. It's built with Express.js and MongoDB, making it scalable and easy to maintain.

## 🚀 Features

- **User Management**
  - User registration and authentication
  - JWT-based authorization
  - User profiles with customizable information

- **Note Management**
  - Create, read, update, and delete notes
  - Automatic pagination of content 
  - Word count tracking
  - Metadata for notes (creation date, modification date)

- **Text Formatting**
  - Multiple text alignment options
  - Adjustable line spacing
  - Text formatting (bold, italic, etc.)
  - Font style customization
  - Text color and background color settings

- **Social Features**
  - Like notes
  - Comment on notes
  - User profiles with profile pictures

## 🛠️ Tech Stack

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - Database with Mongoose ODM
- **JWT** - JSON Web Tokens for authentication
- **bcrypt.js** - Password hashing

## 📁 Project Structure

```
backend/
│
├── server.js           # Entry point for the application
├── db.js               # Database connection configuration
├── package.json        # Project dependencies and scripts
│
├── controller/         # Request handlers
│   ├── userController.js     # User-related controllers
│   ├── noteController.js     # Note-related controllers
│   └── formatController.js   # Text formatting controllers
│
├── middleware/         # Express middleware
│   └── auth.js         # Authentication middleware
│
├── Models/             # MongoDB schemas
│   ├── User.js         # User model
│   └── Notes.js        # Note model
│
└── routes/             # API routes
    ├── users.js        # User routes
    ├── notes.js        # Note routes
    └── format.js       # Text formatting routes
```

## 🔧 Setup and Installation

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)

### Installation

1. Clone the repository:
```
git clone <repository-url>
cd cbackend/backend
```

2. Install dependencies:
```
npm install
```

3. Create a `.env` file in the root directory with the following variables:
```
PORT=5000
MONGO_URL=your_mongodb_connection_string
JWT_SECRET=your_secret_key
NODE_ENV=development
```

4. Start the server:
```
# Development mode with auto-restart
npm run dev

# Production mode
npm start
```

## 📚 API Documentation

### User Routes

- **Register a new user**
  - POST `/api/users`
  - Body: `{ "username": "user1", "email": "user@example.com", "password": "password123" }`

- **Login**
  - POST `/api/users/login`
  - Body: `{ "email": "user@example.com", "password": "password123" }`

- **Get user profile**
  - GET `/api/users/profile`
  - Headers: `x-auth-token: <jwt_token>`

- **Update user profile**
  - PUT `/api/users/profile`
  - Headers: `x-auth-token: <jwt_token>`
  - Body: `{ "username": "updated_username", "email": "new@example.com", "profileImage": "image_url" }`

### Note Routes

- **Get all notes**
  - GET `/api/notes`

- **Get a specific note**
  - GET `/api/notes/:id`

- **Create a new note**
  - POST `/api/notes`
  - Body: `{ "title": "My Note", "content": "Note content...", "language": "en", "fontStyle": "Arial" }`

- **Update a note**
  - PUT `/api/notes/:id`
  - Body: `{ "title": "Updated Title", "content": "Updated content..." }`

- **Delete a note**
  - DELETE `/api/notes/:id`

### Format Routes

- **Format note text**
  - PUT `/api/format/:id/text`
  - Body: `{ "formatType": "bold", "selection": { "start": 10, "end": 20 }, "formattedText": "<b>selected text</b>" }`

- **Change text alignment**
  - PUT `/api/format/:id/alignment`
  - Body: `{ "alignment": "center" }`

- **Change line spacing**
  - PUT `/api/format/:id/spacing`
  - Body: `{ "lineSpacing": 2.0 }`

## 🧪 Testing

You can test the API endpoints using tools like Postman or Insomnia. Make sure to include the authentication token in the header for protected routes.

## 🔒 Authentication

This API uses JWT (JSON Web Token) for authentication. After logging in, include the token in the request header:

```
x-auth-token: your_jwt_token
```

## 📝 License

ISC

## 👨‍💻 Author

Mayank Rathore
