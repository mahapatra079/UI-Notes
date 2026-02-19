 Rest Api  - API calls are made through a UI Service Layer. The UI component triggers a service function on events like 
             page load or button click. 
             The service handles the HTTP request using fetch or Axios, receives the response, and returns the data to the UI. 
             The UI then updates state and re-renders.
             This approach improves separation of concerns, reusability, and maintainability.

A REST API is a backend API that allows applications to communicate over HTTP using standard methods.

| Method | Purpose     |
| ------ | ----------- |
| GET    | Read data   |
| POST   | Create data |
| PUT    | Update data |
| DELETE | Delete data |

Note:  REST API = Server contract
Service API = Client wrapper

Flow :-  

UI (React / Vue)
     ↓
REST API (Backend)

ex:  

REST API (Backend) -  GET /api/users
                    POST /api/users

                    
// userService.js
     export const getUsers = () =>
     fetch("/api/users").then(res => res.json());

     export const createUser = (user) =>
     fetch("/api/users", {
     method: "POST",
     body: JSON.stringify(user)
     });

UI uses Service API -  getUsers().then(users => setUsers(users));

Note:  There are TWO service layers in real systems:

     UI Layer  - (JavaScript (React / Vue))
     UI Service Layer (JavaScript)

     Backend Service Layer (Node.js (JavaScript))
     API Type - (REST API)
     DB - (MongoDB)


Flow -    
     
     React UI (JS)
          ↓
     UI Service Layer (JS)
          ↓
     REST API (Node.js / Express Js)
          ↓
     Database

# REST API Summary

## What is REST API?
Backend API using HTTP methods for client-server communication

## HTTP Methods
| Method | Purpose     |
| ------ | ----------- |
| GET    | Read data   |
| POST   | Create data |
| PUT    | Update data |
| DELETE | Delete data |

## Architecture Layers
```
React UI (JS)
     ↓
UI Service Layer (JS)
     ↓
REST API (Node.js/Express)
     ↓
Database (MongoDB)
```

## Key Concepts
- **REST API:** Server contract (backend endpoints)
- **Service API:** Client wrapper (frontend functions)
- **Separation:** UI triggers → Service handles HTTP → API processes → DB stores

## Example Implementation
```javascript
// userService.js (UI Service Layer)
export const getUsers = () =>
  fetch("/api/users").then(res => res.json());

export const createUser = (user) =>
  fetch("/api/users", {
    method: "POST",
    body: JSON.stringify(user)
  });

// UI Usage
getUsers().then(users => setUsers(users));
```

## Benefits
- Separation of concerns
- Code reusability  
- Better maintainability

**Your API is slow. How will you handle it in frontend?**
