# API (Application Programming Interface)

API is the communication channel between UI & Service Layer.

---

## Flow

1. UI sends Request
2. Server processes
3. Server sends Response

```
UI ------> API Request -------> Server
UI <------ API Response <------- Server
```

---

## Syntax

```
https://egss48ain.ezdev.net/system/ws/v20/admin/7849

Protocol -- https
Domain   -- egss48ain.ezdev.net
Path     -- /system/ws/v20/admin/7849
```

### Protocol = http / https

**Difference B/W https vs http**

**HTTP** - HyperText Transfer Protocol
- data is not secure
- data is visible in plain text
- Default Port => 80

**HTTPS** - HyperText Transfer Secure
- Data is secured
- Data is encrypted using SSL/TLS
- Default Port => 443

**Example:**

If you login using HTTP:
- Anyone on the same WiFi can see your password.

If you login using HTTPS:
- Password is encrypted → cannot be read.

---

## Types Of Parameters in API

### 1. API Without Parameter

Default Page (Home Page)

```
https://egss48ain.ezdev.net/system/v20/admin   (GET)
```

### 2. API With Query Parameter

Starts with ? (?type=omit)

```
https://egss48ain.ezdev.net/system/v20/admin?type=omit (GET)
```

- Used for filtering/searching

### 3. API with Path Parameter

Used to fetch specific resource.

```
https://egss48ain.ezdev.net/system/v20/admin/7849 (GET)
```

> 7849 is a path param (specific admin ID)

### 4. Body Parameter

It will be in JSON Format

```
POST /admin
PUT /admin/7849
```

**Example:**
```json
{
  "name": "amit",
  "age": "20"
}
```

- Body is sent inside request payload.

---

## Types Of API Request

### 1. GET

This is used to get data from server.

**Example:**
```
GET /admin/7849
```
This will fetch admin with ID 7849 from the server.

```
GET /admin?type=omit
```
This will fetch all admins except omitted ones.

**Flow:**
```
UI → API Request → Server → Request → Database

UI ← API Response ← Server ← Response ← Database
```

---

### 2. POST / PUT

This is used save data in the server.
- **POST** - Create new data
- **PUT** - Update existing data

**Example:**

**POST /admin**

Request Body:
```json
{
  "name": "amit",
  "age": 20
}
```
This will create a new admin with name "amit" and age 20.

**PUT /admin/7849**

Request Body:
```json
{
  "name": "amit kumar",
  "age": 21
}
```
This will update admin with ID 7849 to have name "amit kumar" and age 21.

**Flow:**
```
UI → API Request → Server → Stores → Database
UI ← API Response(Optional) ← Server ← Confirmation ← Database

```

---

### 3. PATCH

This is used to partially update data in the server.

**Example:**

**PATCH /admin/7849**

Request Body:
```json
{
  "age": 21
}
```
This will update only age field of admin with ID 7849, while keeping other fields unchanged.

---

### 4. DELETE

This is used to delete data from the server.

**Example:**
```
DELETE /admin/7849
```
This will delete admin with ID 7849 from the server.

---

### Note

**Fixed URL** - Default Page (Home Page)

Example:
```
https://www.youtube.com
```

**Dynamic URL** - Content Changes Dynamically

Example:
```
https://www.youtube.com/watch?v=abc123
```

> watch?v=abc123 - Changes Dynamically

---

### Difference between POST and PUT

**POST** - Creates new data
- POST/users
- Example:
  ```json
  {
    "name": "amit",
    "age": 29
  }
  ```

**PUT** - Updates existing data
- PUT/users/101
- Example:
  ```json
  {
    "name": "amit kumar",
    "age": 30
  }
  ```

> **Note:** POST is used to create a new request; while PUT is used to update an existing resource completely.  
> PUT is idempotent; whereas POST is not idempotent.

> **Note:** PUT replaces the entire object. If you want to update only one field, then use PATCH instead of PUT.

**Example:**
```
PATCH/users/101
```

> **Note:** POST, PUT, PATCH are the BODY Parameter.
       

## Summary

An API is a communication interface between frontend and backend. It uses HTTP methods like GET, POST, PUT, PATCH, and DELETE to perform operations. APIs can accept parameters through path parameters, query parameters, and request body. The typical flow involves the client sending a request, the server processing it, and returning a response.

---

## Flow Diagram

```
React → Axios/Fetch → Backend API → Database

React ← Response ← Backend ← Database
```

---

## Scenario

Let's say user clicks "Create User" button.

1. User clicks button
2. Frontend sends API request (POST /users)
3. Server receives request
4. Server validates data
5. Server saves data in database
6. Server sends response (200 / 201)
7. Frontend updates UI

---

## REST API (Representational State Transfer)

REST API is used for backend communication between frontend and server. It uses HTTP methods to perform operations on resources.

- **GET** - Retrieve data
- **POST** - Create new data
- **PUT** - Update existing data
- **PATCH** - Partially update data
- **DELETE** - Delete data
---

## Database Types

### 1. SQL (Relational Database)
### 2. NoSQL (Non-Relational Database)
### 3. MongoDB (Stores data in JSON-like documents)