# REST API

## What is REST API?

A REST API is a backend API that allows applications to communicate over HTTP using standard methods.

---

## HTTP Methods

| Method | Purpose     |
|--------|-------------|
| GET    | Read data   |
| POST   | Create data |
| PUT    | Update data |
| DELETE | Delete data |

---

## Service Layer Pattern

API calls are made through a UI Service Layer. The UI component triggers a service function on events like page load or button click. The service handles the HTTP request using fetch or Axios, receives the response, and returns the data to the UI. The UI then updates state and re-renders.

> **Note:** REST API = Server contract | Service API = Client wrapper

---

## Architecture Flow

### Simple Flow
```
UI (React / Vue)
     ↓
REST API (Backend)
```

### Complete Flow
```
React UI (JS)
     ↓
UI Service Layer (JS)
     ↓
REST API (Node.js / Express Js)
     ↓
Database (MongoDB)
```

---

## Two Service Layers

| Layer | Technology |
|-------|------------|
| UI Layer | JavaScript (React / Vue) |
| UI Service Layer | JavaScript |
| Backend Service Layer | Node.js (JavaScript) |
| API Type | REST API |
| Database | MongoDB |

---

## Example Implementation

### Backend Endpoints
```javascript
GET  /api/users
POST /api/users
```

### UI Service Layer
```javascript
// userService.js
export const getUsers = () =>
  fetch("/api/users").then(res => res.json());

export const createUser = (user) =>
  fetch("/api/users", {
    method: "POST",
    body: JSON.stringify(user)
  });
```

### UI Usage
```javascript
getUsers().then(users => setUsers(users));
```

---

## Benefits

- Separation of concerns
- Code reusability
- Better maintainability

---

## Handling Slow APIs

### 1. Loading States
```javascript
const [loading, setLoading] = useState(false);
setLoading(true);
const data = await getUsers();
setLoading(false);
```

### 2. Caching
```javascript
const cache = new Map();
if (cache.has('users')) return cache.get('users');
```

### 3. Debouncing
```javascript
const debounce = (func, delay) => {
  let timeoutId;
  return (...args) => {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => func(...args), delay);
  };
};
```

### 4. Pagination
```javascript
fetch(`/api/users?page=${page}&limit=${limit}`);
```

### 5. Optimistic Updates
```javascript
setUsers(users.filter(u => u.id !== id)); // Update UI first
await deleteUserAPI(id); // Then call API
```

---
