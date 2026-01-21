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

css
Copy code

**Request Body:**
```json
{
  "username": "exampleUser",
  "email": "user@example.com",
  "password": "password123"
}
Success Response (201 Created):

json
Copy code
{
  "message": "User registered successfully"
}
Error Responses:

json
Copy code
{
  "error": "Email already exists"
}
json
Copy code
{
  "error": "Username, email, and password are required"
}
2️⃣ Login User
POST /api/auth/login

Headers:

pgsql
Copy code
Content-Type: application/json
Request Body:

json
Copy code
{
  "email": "user@example.com",
  "password": "password123"
}
Success Response (200 OK):

json
Copy code
{
  "token": "<JWT_TOKEN>"
}
Error Responses:

json
Copy code
{
  "error": "Invalid email or password"
}
json
Copy code
{
  "error": "Email and password are required"
}
3️⃣ Get Profile (Protected)
GET /api/auth/profile

Headers:

pgsql
Copy code
Authorization: Bearer <JWT_TOKEN>
Content-Type: application/json
Success Response (200 OK):

json
Copy code
{
  "message": "User profile fetched successfully",
  "user": {
    "id": "USER_ID",
    "username": "exampleUser",
    "email": "user@example.com"
  }
}
Error Responses:

json
Copy code
{
  "error": "No token provided"
}
json
Copy code
{
  "error": "Invalid token"
}
⚡ Example Flow
Register a User

json
Copy code
POST /api/auth/register
{
  "username": "exampleUser",
  "email": "user@example.com",
  "password": "password123"
}
Login

json
Copy code
POST /api/auth/login
{
  "email": "user@example.com",
  "password": "password123"
}
Access Profile

json
Copy code
GET /api/auth/profile
Headers: Authorization: Bearer <JWT_TOKEN>
🛠 Tech Stack
Node.js – JavaScript runtime

Express.js – Web framework

MongoDB Atlas – Cloud database

Mongoose – MongoDB ODM

JWT – JSON Web Tokens for authentication

Postman – API testing

📌 Notes
Passwords are hashed with bcrypt before saving.

Protected routes require a JWT token in the Authorization header.

You can test endpoints locally or via the deployed Render URL.

📄 License
This project is open-source under the MIT License.

yaml
Copy code

---

This version includes:

- **Badges** for Node.js, Express, MongoDB, License  
- **Tables** for endpoints and base URLs  
- **Clear sectioning** for API, tech stack, notes, and license  
- **Anonymous examples**  

---
