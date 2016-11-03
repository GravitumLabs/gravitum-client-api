# Request #

***Request data :*** 

```
#!json

{
  "method":"PushEvent",
  "fields": 
           {
              "push_id": 1,
              "event": 1
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * event - (int) - event name (1 - viewed)
    * push_id - (int) - push id from incoming push data ("push_id" field in json)

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
