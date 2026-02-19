# Microservice Architecture 

How frontend communicates with backend ?

In microservice architecture, frontend communicates with backend via an API Gateway. The gateway routes requests to respective microservices like Order, Payment, or User Service. Each service has its own database and can communicate synchronously using REST or asynchronously using message brokers like Kafka. Services are containerized using Docker and deployed via Jenkins pipelines into Kubernetes clusters. Each service is independently scalable and deployable.


## Frontend Flow

```
User → UI (React/Vue) → API Gateway → Microservices
```

### 1. User Action
```
User clicks: "Place Order"
```

### 2. UI Makes API Call
```javascript
// Frontend (React/Vue) calls:
POST /api/orders

// Using:
- axios
- fetch
- service layer file

// Example:
orderService.placeOrder(data)
```

### 3. Request Flow
```
Component → Service Layer → API Gateway → Microservice
```


##  Frontend Architecture in Microservices

```
┌─────────────────┐
│   Components    │
└────────┬────────┘
         │
         ↓
┌─────────────────┐
│  Service Layer  │  (API calls)
└────────┬────────┘
         │
         ↓
┌─────────────────┐
│  API Gateway    │  (URL)
└────────┬────────┘
         │
         ↓
┌─────────────────┐
│  Microservices  │  (Backend)
└─────────────────┘
```


## Why Service Layer?

**Pattern:**
```
Component → Service File → API
```

**Example:**
```
OrderComponent.vue
       ↓
orderService.ts
       ↓
https://api.myapp.com/orders
```

**Benefits:**
- Separation of concerns
- Reusable API logic
- Easier testing
- Centralized error handling
