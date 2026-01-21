# Bearer Auth MVC

## Overview
This is a **Node.js backend project** implementing **user authentication and authorization** using **JWT (JSON Web Tokens)** and **Bearer tokens**.  
The project follows the **MVC architecture** and uses **MongoDB Atlas** as the database. All APIs are tested using **Postman**.  

---

## Base URL
Local: http://localhost:5000
Deployed: https://your-backend-url.onrender.com

yaml
Copy code

---

## API Endpoints

### 1️⃣ Register User
**POST** `/api/auth/register`  

**Description:** Creates a new user account. Passwords are hashed before storing.

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

Description: Logs in a user and returns a JWT token.

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
3️⃣ Get User Profile (Protected)
GET /api/auth/profile

Description: Retrieves the logged-in user's information. Requires a valid Bearer token.

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
Example Flow
Register

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
Returns:

json
Copy code
{
  "token": "<JWT_TOKEN>"
}
Access Profile

json
Copy code
GET /api/auth/profile
Headers: Authorization: Bearer <JWT_TOKEN>
Returns:

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
Notes
All passwords are hashed using bcrypt before saving.

Protected routes require a valid JWT token in the Authorization header.

You can test endpoints using Postman with either the local URL or the deployed Render URL.

Tech Stack
Node.js

Express.js

MongoDB Atlas (Mongoose)

JWT (JSON Web Tokens)

Postman (for API testing)

