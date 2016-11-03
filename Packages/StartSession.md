# Request #

***Request data :*** 

```json

{
  "method":"StartSession",
  "fields": 
           {
              "user": "user_server_id"
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * user - (string) - server user id from [Auth](https://bitbucket.org/autopushteam/backend/wiki/Packages/Auth)

# Response #

***Response data :*** 


```json

{
  "method":"StartSession",
  "error":
          {
            "status":false,
            "message":"",
            "code":0
          },
  "data": {
              "session": "server_session_id"
           }
}
```

***Response fields :*** 

* method - Request method
* error - Request errors
    * status - (bool) - true/false
    * message - (string) - error message if exists
    * code - (int) - error code
* data - (array) - Response data
    * session - (string) - session server id
