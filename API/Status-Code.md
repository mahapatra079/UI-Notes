# Status Code

 Status code in API response tells whether the request was successful or failed, and helps the client handle the response

## Types of Status Codes
- **1xx** - Informational
- **2xx** - Success
- **3xx** - Redirection
- **4xx** - Client Error
- **5xx** - Server Error

### 1. 1xx - Informational
This means the request was received and is being processed.
### 2. 2xx - Success
This means the request was successfully processed by the server.
### 3. 3xx - Redirection
This means the client needs to take additional action to complete the request.
### 4. 4xx - Client Error
This means the request was invalid or cannot be processed by the server.
### 5. 5xx - Server Error
This means the server encountered an error while processing the request.

### Most Common Status Codes
  
- **200 OK** - The request was successful and the server returned the requested data.

- **201 Created** - The request was successful and a new resource was created.

- **204 No Content** - The request was successful but there is no content to return.

- **400 Bad Request** - The request was invalid or cannot be processed by the server.

- **401 Unauthorized** - The client must authenticate itself to get the requested response.

- **403 Forbidden** - The client does not have access rights to the content.

- **404 Not Found** - The server can not find the requested resource.

- **500 Internal Server Error** - The server encountered an error while processing the request.

- **503 Service Unavailable** - The server is not ready to handle the request, often due to maintenance or overload.

- **504 Gateway Timeout** - The server did not receive a timely response from an upstream server while acting as a gateway or proxy.

- **505 HTTP Version Not Supported** - The server does not support the HTTP protocol version used in the request.

- **511 Network Authentication Required** - The client needs to authenticate to gain network access.


### Why Status Code is Important?
- To show success message
- To show error message
- To handle response in frontend
- To debug issues in API
- To improve user experience by providing feedback on the outcome of their actions.

## Conclusion
Status codes are essential for understanding the outcome of an API request. They help the client determine how to handle the response and whether any further action is needed. Always refer to the status code documentation for your specific API to understand what each code means in the context of that API.

## Example Responses

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
  "message": "Success",
  "data": [...]
}
```

---