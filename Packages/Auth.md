# Request #

***Request data :*** 

```json

{
  "method":"Auth",
  "fields": 
           {
              "user_id": "some_user_id",
              "user_birthday": 99999999999,
              "user_gender": 0,
              "user_name": "some_user_name",
              "user_facebook_id": "user_facebook_id",
              "device_id": "device_id",
              "device_push_token": "device_push_token",
              "device_height": 500,
              "device_width": 1000,
              "device_os": 1,
              "device_os_version":"version",
              "device_manufacturer":"device_manufacturer",
              "device_model":"device_model",
              "device_language":"en-US",
              "device_country_code":"UA",
              "device_timezone":3600
           }
}

```

***Request fields :*** 

* method - Request method
* fields - Request fields
    * user_id - (string) - unique user id
    * user_birthday - (int) - user birthday (timestamp, 0 by default)
    * user_gender - (int) - user gender (0 - default (none), 1 - male, 2 - female)
    * user_name - (string) - user name (empty string by default)
    * user_facebook_id - (string) - facebook user id (empty string by default)
    * device_push_token - (string) - device push token
    * device_id - (string) - device id
    * device_height - (int) - device height
    * device_width - (int) - device width
    * device_os - (int) - device os (1 - ios, 2 - android)
    * device_os_version - (string) - os version
    * device_manufacturer - (string) - device manufacturer
    * device_model - (string) - device model
    * device_language - (string) - device language (2 character)
    * device_country_code - (string) - device country code (two-letter (ISO 3166-1 alpha-2))
    * device_timezone - (int) - number of seconds from UTC

# Response #

***Response data :*** 


```json

{
  "method":"Auth",
  "error":
          {
            "status":false,
            "message":"",
            "code":0
          },
  "data": {
              "user": "user_server_id"
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
    * user - (string) - server user id
