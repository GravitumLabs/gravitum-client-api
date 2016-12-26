# Request #

***Request data :*** 

```json

{
  "method":"SetCustomFields",
  "fields": 
           {
              "user": "user_server_id",
              "fields": {"key":"value", "key2":"value2"..}
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * user - (string) - server server id
    * fields - (array) - array of the user custom fields (limit 15 fields)

# Response #

***Response data :*** 


```json

{
  "method":"SetCustomFields",
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
