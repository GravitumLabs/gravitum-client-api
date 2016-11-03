# Request #

***Request data :*** 

```
#!json

{
  "method":"AddEvent",
  "fields": 
           {
              "user": "user_server_id",
              "session": "session_server_id",
              "event": "init",
              "data": {"key1":"value1","key2":"value2"}
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * user - (string) - server server id
    * session - (string) - session server id
    * event - (string) - event name
    * data - (array) - array of event data

# Response #

***Response data :*** 


```
#!json

{
  "method":"AddEvent",
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
    * status - (bool) - true/false
