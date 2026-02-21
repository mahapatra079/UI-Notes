# API = Application Programming Interface
  
 1) API = API is the communication channel between UI & Service Layer
 
 2) Flow :> 

            UI ------> API Request -------> Server
            UI <------ API Response <------- Server

     - UI sends Request

     - Server processes

     - Server sends Response

 3) Syntax : 

           https://egss48ain.ezdev.net/system/ws/v20/admin/7849

           Protocol -- https
           Domaion  -- egss48ain.ezdev.net
           Path -- /system/ws/v20/admin/7849

    => Protocol = http / https

          --> Difference B/W https vs http

            HTTP - HyperText Transfer Protocol
                 - data is not secure
                 - data is visible in plain text
                 - Default Port => 80
                 
            HTTPS - HyperText Transfer Secure
                  - Data is secured
                  - Data is encrypted using SSL/TLS
                  - Default Port => 443
                  
          Ex: 
                If you login using HTTP:

                 - Anyone on the same WiFi can see your password.

                If you login using HTTPS:

                 - Password is encrypted → cannot be read.

 4) Types Of Parameters in API:

                 1) API Without Parameter - Default Page (Home Page)

                        ex: https://egss48ain.ezdev.net/system/v20/admin   (GET)
                
                 2) API With Query Parameter - starts with ? (?type=omit)

                        ex: https://egss48ain.ezdev.net/system/v20/admin?type=omit (GET)

                        - Used for filtering/searching

                 3) API with Path Parameter - Used to fetch specific resource.
                        
                        ex: https://egss48ain.ezdev.net/system/v20/admin/7849 (GET)

                          => 7849 is a path param (specific admin ID)

                 4) Body Parameter - It will be in JSON Format

                            POST /admin
                            PUT /admin/7849
                  
                        Ex: 
                              {
                                "name": "amit",
                                "age": "20"
                              }
                      
                      - Body is sent inside request payload.



# Summary 
           An API is a communication interface between frontend and backend. It uses HTTP methods like GET, POST, PUT, PATCH, and DELETE to perform operations.
           APIs can accept parameters through path parameters, query parameters, and request body. The typical flow involves the client sending a request,
           the server processing it, and returning a response.

# Flow 
        React → Axios/Fetch → Backend API → Database
        React ← Response ← Backend ← Database

# Scenario - Let’s say user clicks "Create User" button.

           - User clicks button
           - Frontend sends API request (POST /users)
           - Server receives request
           - Server validates data
           - Server saves data in database
           - Server sends response (200 / 201)
           - Frontend updates UI