# Courses API

## Description
This project is an API for managing courses and users, built using Node.js, Express, and MongoDB. It provides functionalities to manage courses and users, including authentication, authorization, and CRUD operations.

## Table of Contents
1. [Features](#features)
2. [Technologies](#technologies)
3. [Installation](#installation)
4. [Environment Variables](#environment-variables)
5. [Middleware](#middleware)
6. [Error Handling](#error-handling)

## Features
- Manage courses (add, update, delete, get all courses, get specific course).
- User authentication and authorization (register, login).
- Role-based access control (admin, manager, user).
- JSON Web Token (JWT) for secure authentication.
- Pagination support for retrieving users and courses.
  
## Technologies
- **Node.js**
- **Express.js**
- **MongoDB**
- **Mongoose** (ODM)
- **bcryptjs** (for password hashing)
- **JWT** (for authentication)
- **express-validator** (for validation)
- **Multer** (for handling file uploads)

## Installation
To install and run this project locally:

1. Clone the repository:
    ```bash
    git clone https://github.com/amiraa205/courses-api.git
    ```

2. Navigate into the project directory:
    ```bash
    cd courses-api
    ```

3. Install the dependencies:
    ```bash
    npm install
    ```

4. Create a `.env` file and add the required environment variables (see below).

5. Run the server:
    ```bash
    npm start
    ```

By default, the project will run on `http://localhost:3000`.

## Environment Variables
You need to set up the following environment variables in your `.env` file:

```plaintext
PORT=3000
MONGO_URI=mongodb+srv://yourmongodburl
JWT_SECRET_KEY=your_jwt_secret_key
 ```

## Middleware

- **verifyToken**: Middleware to validate JWT and protect routes.
  - **Usage**: Apply to routes that require authentication.
  - **Functionality**: Checks for a valid JWT in the `Authorization` header and adds the user information to the request.

- **allowedTo**: Middleware for role-based access control.
  - **Usage**: Apply to routes that require specific user roles.
  - **Functionality**: Verifies if the user has the necessary role to access the route.

- **asyncWrapper**: Error handling middleware for asynchronous functions.
  - **Usage**: Wrap async route handlers with `asyncWrapper` to handle errors centrally.

## Error Handling

The project uses a custom error handling mechanism with the `AppError` class to standardize error responses. Errors are caught and handled centrally using the `asyncWrapper` middleware to ensure consistent error handling across asynchronous routes.

- **AppError Class**: Defines the structure of error responses.
  - **Usage**: Create custom error instances with a message, status code, and status text.
  - **Example**:
    ```js
    const appError = new AppError();
    throw appError.create('Error message', 400, 'fail');
    ```
