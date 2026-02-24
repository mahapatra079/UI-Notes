# GraphQL

GraphQL is a Query Language for API and runtime for executing those queries.

**Note:** It allows client (Frontend) to request exactly what they need.

## 1) Difference between GraphQL vs REST API

### REST API
- Multiple Endpoints
- Over-fetching (extra data)
- Under-fetching of data (need multiple requests)

### GraphQL
- Single Endpoint
- Client controls the data
- One request → exact required data

## 2) GraphQL Work Flow

1. Client sends a query to the server.
2. Server validates against schema.
3. Resolvers fetch data.
4. Server returns JSON response.

```
Client → GraphQL Query → Server → Resolver → Database → JSON
```

## 3) GraphQL Schema

Defines types, queries, and mutations.

```graphql
type User {
    id: ID!
    name: String!
    email: String!
}

type Query {
    users: [User]
    user(id: ID!): User
}

type Mutation {
    createUser(name: String!, email: String!): User
}
```

## 4) GraphQL Query Example

Query (GET data):

```graphql
query {
    users {
        id
        name
    }
}
```

## 5) Mutation (Create/Update/Delete)

```graphql
mutation {
    createUser(name: "Amit") {
        id
        name
    }
}
```

## 6) Resolver

Functions that fetch actual data.

```javascript
const resolvers = {
    Query: {
        users: () => User.findAll(),
        user: (parent, args) => User.findById(args.id),
    },
    Mutation: {
        createUser: (parent, args) => User.create(args),
    },
};
```

## 7) GraphQL Response Example

**400 Bad Request:**
```json
{
    "status": 400,
    "message": "Email is required"
}
```

**201 Created:**
```json
{
    "status": 201,
    "message": "User created successfully"
}
```

**200 OK:**
```json
{
    "status": 200,
    "data": {
        "users": [
            { "id": 1, "name": "Amit" }
        ]
    }
}
```

## When to Use GraphQL?

- Large frontend apps
- Multiple clients (web + mobile)
- Complex data relationships
- Performance-sensitive apps

## When to Avoid GraphQL?
- Simple APIs
- Real-time data (use WebSockets)
- Caching needs (REST is easier)
- File uploads (GraphQL can be complex)


## Conclusion

If the project is simple and resource-based, I prefer REST for simplicity.
But for complex frontend-driven applications where performance and flexibility matter, GraphQL is more efficient