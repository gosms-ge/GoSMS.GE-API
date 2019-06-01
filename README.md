## Contributing [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/gosms-ge/GoSMS.GE-API/issues)

[![PHP version](https://badge.fury.io/ph/levart%2Fgo-sms-api.svg)](https://badge.fury.io/ph/levart%2Fgo-sms-api)
[![GitHub version](https://badge.fury.io/gh/gosms-ge%2FGoSMS.GE-API.svg)](https://badge.fury.io/gh/gosms-ge%2FGoSMS.GE-API)

# GoSMS API


GoSMS API is build for GoSMS - Bulk SMS Application For Marketing


### Prerequisites

To run GoSMS API you have to install GoSMS Application on your server. 
```
php >=5.6
GoSMS - Bulk SMS Application For Markting
```

### Installing
Via Composer
```
composer require levart/go-sms-api
```

And Via Bash

```
git clone https://github.com/gosms-ge/GoSMS.GE-API.git
```

## Usage


 ### Step 1:
If install GoSMS API using Git Clone then load your GoSMS API Class file and Use namespace. 
```php
require_once 'src/Class_Go_SMS_API.php';
use GoSMS\GoSMSAPI;
```
If install GoSMS API using Composer then Require/Include autoload.php file in the index.php of your project or whatever file you need to use **GoSMS API** classes:. 
```php
require 'vendor/autoload.php';
use GoSMS\GoSMSAPI;
```
### Step 2:
set your API_KEY from `https://mywebhost.com/sms-api/info` (your application install url)
```php
$api_key = 'YWRtaW46YWRtaW4ucGFzc3dvcmQ=';
```
### Step 3:
Change the from number below. It can be a valid phone number or a String
```php
$from = '8801721000000';
```

### Step 4:
the number we are sending to - Any phone number
```php
$destination = '8801810000000';
```
You have to must include Country code at beginning of the phone number.  

### Step 5:
Replace your Install URL like `https://mywebhost.com/sms/api` is mandatory on your install url


// SMS Body
```php
$sms = 'test message from GoSMS';
```
// Unicode SMS
```php
$unicode = '0'; //For plain message
$unicode = '1'; //For Unicode message
```
// Create SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'unicode' => $unicode,
);
```

### Step 6: 
Instantiate a new GoSMS API request
```php
$client = new GoSMSAPI();
```

## Send SMS
Finally send your sms through GoSMS API
```php
$response = $client->send_sms($sms_body, $url);
```

## Get Inbox
Get your all message
```php
$get_inbox=$client->get_inbox($api_key,$url);
```

## Get Balance
Get your account balance
```php
$get_balance=$client->check_balance($api_key,$url);
```
## Response
GoSMS API return response with `json` format, like:

```json
{"code":"ok","message":"Successfully Send"}
```

## Status Code

| Status | Message |
| --- | --- |
| `ok` | Successfully Send |
| `100` | Bad gateway requested |
| `101` | Wrong action |
| `102` | Authentication failed |
| `103` | Invalid phone number |
| `104` | Phone coverage not active |
| `105` | Insufficient balance |
| `106` | Invalid Sender ID |

## Authors

* **Levan Jmukhadze** - *Initial work* - [levart](https://github.com/levart)
