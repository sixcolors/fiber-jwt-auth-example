# GoFiber JWT Role-Based Access Control (RBAC) Example

This is a simple example of a Go application using the GoFiber framework, JWT (JSON Web Tokens), and a custom middleware function to implement Role-Based Access Control (RBAC).

## Overview

The application sets up a few routes:

- `/login`: This route accepts POST requests with a user and pass form data. If the credentials match a hardcoded "john" and "doe", it generates a JWT with claims including the user's name and roles, and returns it in the response. The JWT is signed with a secret key.

- `/`: This is an unauthenticated route that anyone can access.

- `/restricted`: This route is protected by a JWT middleware and a custom hasRole middleware. The JWT middleware checks if the request has a valid JWT in the Authorization header. The hasRole middleware checks if the JWT has a claim of a specific role.

## Middleware

The hasRole middleware function checks if the JWT has a claim of a specific role. It can be applied to any route. If the JWT does not have the required role, it returns a 403 Forbidden status.

## JWT

The JWT is generated in the /login route. It includes claims of the user's name and roles. The JWT is signed with a secret key.

## Running the Application

To run the application, you need to have Go installed. You can run the following commands:

```bash
go run main.go
```

The application will start on port 3000.

## Testing

You can test the application with curl:

```bash
# and get a token
curl --data "user=john&pass=doe" http://localhost:3000/login

# Access the restricted route with the token
curl localhost:3000/restricted -H "Authorization: Bearer <token>"
```

## License

This project is licensed under the MIT License