# 🔐 Bearer Auth MVC

[![Node.js](https://img.shields.io/badge/Node.js-14.x-green)](https://nodejs.org/) 
[![Express](https://img.shields.io/badge/Express-4.x-blue)](https://expressjs.com/) 
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-brightgreen)](https://www.mongodb.com/cloud/atlas) 
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 📖 Overview
**Bearer Auth MVC** is a **Node.js backend project** demonstrating **user authentication and authorization** using **JWT (JSON Web Tokens)** and **Bearer tokens**.  

The project follows the **MVC architecture**, uses **MongoDB Atlas** for the database, and includes fully functional APIs for:

- User Registration  
- User Login  
- Protected Profile Route  

All APIs are tested using **Postman**.

---

## 🌐 Base URLs

| Environment | URL |
|-------------|-----|
| Local       | `http://localhost:5000` |
| Deployed    | `https://your-backend-url.onrender.com` |

---

## 📌 API Endpoints

| Method | Endpoint | Description | Protected |
|--------|---------|------------|-----------|
| POST   | `/api/auth/register` | Register a new user | ❌ No |
| POST   | `/api/auth/login`    | Login and get JWT token | ❌ No |
| GET    | `/api/auth/profile`  | Fetch logged-in user's profile | ✅ Yes |

---

### 1️⃣ Register User
**POST** `/api/auth/register`  

**Headers:**
Content-Type: application/json


**Request Body:**
```json
{
  "username": "exampleUser",
  "email": "user@example.com",
  "password": "password123"
}
```

Success Response (201 Created):
```
{
  "message": "User registered successfully"
}
```

Error Responses:
```
{
  "error": "Email already exists"
}

{
  "error": "Username, email, and password are required"
}
```
2️⃣ Login User

POST /api/auth/login

Headers:

Content-Type: application/json


Request Body:
```
{
  "email": "user@example.com",
  "password": "password123"
}
```

Success Response (200 OK):
```
{
  "token": "<JWT_TOKEN>"
}
```

Error Responses:
```
{
  "error": "Invalid email or password"
}
```
```
{
  "error": "Email and password are required"
}
```
3️⃣ Get Profile (Protected)

GET /api/auth/profile

Headers:

Authorization: Bearer <JWT_TOKEN>
Content-Type: application/json


Success Response (200 OK):
```
{
  "message": "User profile fetched successfully",
  "user": {
    "id": "USER_ID",
    "username": "exampleUser",
    "email": "user@example.com"
  }
}
```

Error Responses:
```
{
  "error": "No token provided"
}

{
  "error": "Invalid token"
}
```
⚡ Example Flow

Register a User
```
POST /api/auth/register
{
  "username": "exampleUser",
  "email": "user@example.com",
  "password": "password123"
}
```

Login

POST /api/auth/login
```
{
  "email": "user@example.com",
  "password": "password123"
}
```

Returns:
```
{
  "token": "<JWT_TOKEN>"
}
```

Access Profile

GET /api/auth/profile
Headers: Authorization: Bearer <JWT_TOKEN>


Returns:
```
{
  "message": "User profile fetched successfully",
  "user": {
    "id": "USER_ID",
    "username": "exampleUser",
    "email": "user@example.com"
  }
}
```
🛠 Tech Stack

Node.js – JavaScript runtime

Express.js – Web framework

MongoDB Atlas – Cloud database

Mongoose – MongoDB ODM

JWT – JSON Web Tokens for authentication

Postman – API testing

📌 Notes

Passwords are hashed with bcrypt before saving.

Protected routes require a valid JWT token in the Authorization header.

You can test endpoints using Postman, locally or via the deployed Render URL.

📄 License

This project is open-source.
