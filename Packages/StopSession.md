# Request #

***Request data :*** 

```
#!json

{
  "method":"StopSession",
  "fields": 
           {
              "session": "session_server_id"
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * session - (string) - server session id

# Response #

***Response data :*** 


```
#!json

{
  "method":"StartSession",
  "error":
          {
            "status":false,
            "message":"",
            "code":0
          },
  "data": {
              "status": true
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
    * status - (bool) - response status