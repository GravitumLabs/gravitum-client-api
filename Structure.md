-----------------------------------------------------------------------------------------------------------
### Request URL ###

Main server - https://apiv2.gravitum.com/init


### Request type ###

**POST**

### Request header ###

List of required header fields: 

* secret - **required** - request secret, HMAC-SHA256 hex from request data with secret key. See [code snippets](https://github.com/GravitumLabs/gravitum-client-api/blob/master/Creating_Secret_Hex_Hashes.md)
* token - **required** - project token given by admin panel
* platform - **required** - device platform (1 - ios, 2 - android)

### Request structure ###

Client should to put json object to the post field "data" or just to the post body

```json

{
    "method":"Auth",
    "fields":{
               "device_id":"123",
               "device_os":"ios"
             }
}
```

### Response type ###

**JSON**

### Response header ###

* secret - **required** - response secret, HMAC-SHA256 hex from request data with secret key
* time - ***required** - server time

### Response structure ###


```json

{
    "method":"Auth",
    "error": {
               "status":true,
               "message":"Missing required fields",
               "code":403
             },
    "data":{}
}
```

* data - **required** - response data

* error - **required** - response error
    
    * "status" - **required** - error status (true/false) 
    * "message" - **required** - error message text
    * "code" - **required** - error code

* method - **required** - response method
