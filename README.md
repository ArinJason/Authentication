Bearer Auth MVC - API Documentation
Base URL
Local: http://localhost:5000
Deployed: https://authentication-h0px.onrender.com

1️⃣ Register User

Endpoint: /api/auth/register

Method: POST

Description: Creates a new user account. Password is hashed before saving.

Headers:

Content-Type: application/json


Request Body (JSON):

{
  "username": "TestUser",
  "email": "testuser@gmail.com",
  "password": "123456"
}


Success Response (201 Created):

{
  "message": "User registered successfully"
}


Error Responses:

400 Bad Request: Missing required fields

{
  "error": "Username, email, and password are required"
}


409 Conflict: Email already exists

{
  "error": "Email already exists"
}

2️⃣ Login User

Endpoint: /api/auth/login

Method: POST

Description: Logs in a user and returns a JWT token for authentication.

Headers:

Content-Type: application/json


Request Body (JSON):

{
  "email": "testuser@gmail.com",
  "password": "123456"
}


Success Response (200 OK):

{
  "token": "<JWT_TOKEN>"
}


Error Responses:

400 Bad Request: Missing email or password

{
  "error": "Email and password are required"
}


401 Unauthorized: Invalid credentials

{
  "error": "Invalid email or password"
}

3️⃣ Get User Profile (Protected)

Endpoint: /api/auth/profile

Method: GET

Description: Retrieves the logged-in user's information. Requires Bearer token in headers.

Headers:

Authorization: Bearer <JWT_TOKEN>
Content-Type: application/json


Success Response (200 OK):

{
  "message": "User profile fetched successfully",
  "user": {
    "id": "642abcd12345",
    "username": "TestUser",
    "email": "testuser@gmail.com"
  }
}


Error Responses:

401 Unauthorized: Missing token

{
  "error": "No token provided"
}


403 Forbidden: Invalid or expired token

{
  "error": "Invalid token"
}

4️⃣ Notes / Additional Info

Password Security: All passwords are hashed with bcrypt before storing.

JWT Token: Use the token received from /login for all protected routes.

Error Handling: Each endpoint returns proper HTTP status codes and descriptive messages.

Testing: You can test all endpoints with Postman using either local URL or deployed URL.

Example API Flow

Register

POST /api/auth/register
{
  "username": "exampleUser",
  "email": "user@example.com",
  "password": "password123"
}


Login

POST /api/auth/login
{
  "email": "user@example.com",
  "password": "password123"
}


Returns:

{
  "token": "<JWT_TOKEN>"
}


Access Profile

GET /api/auth/profile
Headers: Authorization: Bearer <JWT_TOKEN>


Returns:

{
  "message": "User profile fetched successfully",
  "user": {
    "id": "USER_ID",
    "username": "exampleUser",
    "email": "user@example.com"
  }
}
