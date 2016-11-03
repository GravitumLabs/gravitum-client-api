# Request #

***Request data :*** 

```
#!json

{
  "method":"AddPurchase",
  "fields": 
           {
              "user": "user_server_id",
              "session": "session_server_id",
              "product_id": "product_id",
              "price": 9.99,
              "currency": "USD"
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * user - (string) - server server id
    * session - (string) - session server id
    * product_id - (string) - product id
    * price - (double) - product price
    * currency - (string) - product currency

# Response #

***Response data :*** 


```
#!json

{
  "method":"AddPurchase",
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
