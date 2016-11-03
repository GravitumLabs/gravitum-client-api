#### PYTHON ####
```python
# This is a simple example explaining how to
# use the Gravitum REST API to register a device
# start a session, send a custom event & finally
# close the session
import json , hmac , hashlib , requests

def sendGravitumRequest(url,data,token,secret,platform):
	json_data = json.dumps ( data , sort_keys = True , indent = 4 , separators = (',' , ': ') )
	siq = hmac.new ( secret , json_data , hashlib.sha256 ).hexdigest ( )
	header = {
		'secret' : siq ,
		'token' : token ,
		'platform' : platform
	}
	req = requests.post ( url = url , headers = header , data = json_data )
	json_response=json.loads(req.text,encoding = 'unicode')
	return [ json_response , req.status_code , req.reason ]

# Setup Authentication information
# This is available on the admin.gravitum.com dashboard for your game
token = 'c4d6a001256f1fbc59dc4f2c283c28fd'
secret = '461b43e0dbe220a54987aa022d3863c16ecfa37f7e8bbeed55732b11d0cb40c4'
url = 'https://apiv2.gravitum.com/init'


# Register this user and device with Gravitum
# Note: You only need to register the user once.
#
#Initialize Gravitum with relevant player data from your game below
platform =1
init_data = {
  "method":"Auth",
  "fields":
           {
              "user_id": "some_user_id",
              "user_birthday": 99999999999,
              "user_gender": 2,
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
[init_response,init_status,init_reason]=sendGravitumRequest(url,init_data,token,secret,platform)
user_server_id=init_response['data']['user'] #Capture this user's Gravitum Server ID
print 'Gravitum UserID: '+user_server_id

# Start a new session
start_session_data={
  "method":"StartSession",
  "fields":
           {
              "user": user_server_id
           }
}
[ss_response,ss_status,ss_reason] =sendGravitumRequest(url,start_session_data,token,secret,platform)
session_server_id=ss_response['data']['session'] #Capture the current Gravitum session ID
print 'Gravitum SessionID: '+ session_server_id

# Send a custom event
custom_event_data={
  "method":"AddEvent",
  "fields":
           {
              "user": user_server_id,
              "session": session_server_id,
              "event": "Event Name",
              "data": {"key1":"someString","key2":12345}
           }
}
print sendGravitumRequest(url,custom_event_data,token,secret,platform)


#Inform Gravitum when the current session is over
stop_session_data={
  "method":"StopSession",
  "fields":
           {
              "session": session_server_id
           }
}
print sendGravitumRequest(url,stop_session_data,token,secret,platform)
```
