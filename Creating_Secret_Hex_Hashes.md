####Examples of creating hex hashes using HMAC SHA256 in different languages ####


Result for each language should look like 

559568a5a6da9adf750830822124b8294f8374d39a977b5ee1595105bf19b762


With a key = 'YOUR_SECRET_KEY' and data = 'YOUR_REQUEST_JSON_DATA'

#### PHP ####


```php
<?php
$secret_key = 'YOUR_SECRET_KEY';
$json_data = 'YOUR_REQUEST_JSON_DATA';

$secret = hash_hmac('sha256', $json_data, $secret_key);

echo $secret;

```
#### PYTHON ####
```python
import json , hmac , hashlib
# Setup Authentication information
# This is available on the admin.gravitum.com dashboard for your game
secret_key = 'YOUR_SECRET_KEY'
# Convert your data into json
json_data = json.dumps ( data , sort_keys = True , indent = 4 , separators = (',' , ': ') )
secret = hmac.new ( secret_key , json_data , hashlib.sha256 ).hexdigest ( )
```

#### PERL ####


```perl

#!/usr/bin/perl
# your code goes here
use strict;

use Digest::SHA qw(hmac_sha256_hex);

my $secret_key = 'YOUR_SECRET_KEY';
my $json_data = 'YOUR_REQUEST_JSON_DATA';

my $secret = hmac_sha256_hex($json_data, $secret_key);

print "$secret";
```

#### RUBY ####


```ruby

# your code goes here
require 'openssl'
 
secret_key = 'YOUR_SECRET_KEY';
json_data = 'YOUR_REQUEST_JSON_DATA';
 
hash  = OpenSSL::HMAC.hexdigest(OpenSSL::Digest.new('sha256'), secret_key, json_data)
 
puts hash

```


#### JAVA ####

dependency:

compile 'commons-codec:commons-codec:1.9'

ref: 

http://mvnrepository.com/artifact/commons-codec/commons-codec/1.9

```java

import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import org.apache.commons.codec.binary.Base64;

public class Api {
  public static void main(String[] args) {

        String secret_key = "YOUR_SECRET_KEY";
        String json_data = "YOUR_REQUEST_JSON_DATA";
        String digest = null;
        try {
            SecretKeySpec key = new SecretKeySpec((secret_key).getBytes("UTF-8"), "HmacSHA256");
            Mac mac = Mac.getInstance("HmacSHA256");
            mac.init(key);

            byte[] bytes = mac.doFinal(json_data.getBytes("ASCII"));

            StringBuffer hash = new StringBuffer();
            for (int i = 0; i < bytes.length; i++) {
                String hex = Integer.toHexString(0xFF & bytes[i]);
                if (hex.length() == 1) {
                    hash.append('0');
                }
                hash.append(hex);
            }
            digest = hash.toString();
        } catch (UnsupportedEncodingException e) {
        } catch (InvalidKeyException e) {
        } catch (NoSuchAlgorithmException e) {
        }
        System.out.println(digest);
    }
}
```

#### C# ####

```c#

string message = "YOUR_REQUEST_JSON_DATA";
string key = "YOUR_SECRET_KEY";
            
byte[] encodedKey = new ASCIIEncoding().GetBytes(key);
byte[] encodedMessage = new ASCIIEncoding().GetBytes(message);


var hash = new HMACSHA256(encodedKey);
var secret = hash.ComputeHash(encodedMessage);
string secretHash = BitConverter.ToString(secret).Replace("-", "").ToLower();
          
Console.WriteLine(secretHash);
```

#### Objective C ####

```smalltalk

#import <Foundation/Foundation.h>
#import <CommonCrypto/CommonHMAC.h>

+(NSString*)hmac:(NSString*)key :(NSString*)data{
    NSData * nKey = [key dataUsingEncoding:NSASCIIStringEncoding];
    NSData * cData = [data dataUsingEncoding:NSASCIIStringEncoding];

    NSMutableData * hash = [NSMutableData dataWithLength:CC_SHA256_DIGEST_LENGTH];
    CCHmac(kCCHmacAlgSHA256, nKey.bytes, nKey.length, cData.bytes, cData.length, hash.mutableBytes);
    NSString * result = [hash base64EncodedStringWithOptions:0];
    result = [self ByteToString:hash];
    result = [result lowercaseString];
  
    return result;
}

+(NSString*) ByteToString:(NSData*)cData{
    NSUInteger capacity = cData.length *2;
    NSMutableString *sbuf = [NSMutableString stringWithCapacity: capacity];
    const unsigned char *buf = cData.bytes;
    NSInteger i;
    for(i=0; i<cData.length; ++i){
        [sbuf appendFormat:@"%02x", buf[i]];
    }
    return sbuf;
}
```





