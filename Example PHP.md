### Example how to send first request to API server on PHP ###


```php

<?php
/**
 * Setup this from projects list page
 */
const REQUEST_SECRET = 'your_secret_key';
const REQUEST_TOKEN = 'your_token';
const REQUEST_PLATFORM = 'your_platform';


/**
 * Initial auth request, you can put in data one of examples with changing inner data
 */
$data = [
    'method' => 'Auth',
    'fields' => [
        'user_id' => '999_999_999',
        'user_birthday' => 684288379,
        'user_gender' => 'client_user_id',
        'user_name' => 'client_user_name',
        'user_facebook_id' => 999999999,
        'device_id' => 'client_device_id',
        'device_push_token' => 'client_push_token',
        'device_manufacturer' => 'LGE',
        'device_model' => 'Nexus 5',
        'device_height' => 768,
        'device_width' => 1024,
        'device_os' => 2,
        'device_os_version' => '6.0.1',
        'device_language' => 'ua',
        'device_timezone' => 3600,
        'device_country_code' => 'UA'
    ]
];
/**
 * Convert request data to json
 */
$json = json_encode($data);

/**
 * Generate secret key
 */
$siq = hash_hmac('sha256', $data, REQUEST_SECRET);
/**
 * Generate post data
 */
$post = array('data' => $json);
/**
 * Generate header data
 */
$header = [
    'secret: ' . $siq,
    'token: ' . REQUEST_TOKEN,
    'platform: ' . REQUEST_PLATFORM
];
/**
 * Send request via curl
 */
$curl = curl_init();

curl_setopt_array($curl, array(
        CURLOPT_RETURNTRANSFER => 1,
        CURLOPT_HEADER => 0,
        CURLOPT_HTTPHEADER => $header,
        CURLOPT_URL => "https://apiv2.gravitum.com/init",
        CURLOPT_POST => true,
        CURLOPT_POSTFIELDS => $post
    )
);
/**
 * Echo request response
 */
echo curl_exec($curl);

```
