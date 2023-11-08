# Welcome to EvilNet DNSBL API Doc

We want to tell you that we who love IRC find this social network as it is a way of communicating where we prioritize pure text over any other existing format on the internet.
We believe in respect and fun without disturbing anyone. The possibility of chatting on multiple channels and privately between us, makes it our choice.
We affirm the concept of privacy and for that reason, your conversations will always be kept that way, for you, when you choose to chat with someone in a private window.
You should know that in public channels (a main window) we treat each other kindly and respectfully. We hope that you have a good time at Evilnet and of course, we thank you for being part of our network.

**What you can't do:**
- a) Not to damage in any way the network resources or any of its services.
- b) Do not carry out or spread illegal or prohibited activities by local and/or international laws.
- c) Do not hit/attack any user or Evilnet staff.

**We reserve the right to cease any conduct that we detect in the previous points and report it to the authorities that we consider.**

**What you can do:**
Everything else, have a good time, fun and above all, make friends :)

**EvilNet DNSBL – What is it?**

EvilNET DNSBL is a collection of compromised ips obtained using different sources with the purpose of maintaining a black list of unwanted clients in our network.

**Why having a DNSBL on EvilNet?**

As we have said, we have DNSBL to take care of the resources of our network and prevent new attacks from the IPs involved in previous attacks. It helps us protect our resources and prevent damage to both our equipment and users or staff. In addition to this, a registry is very useful to facilitate it to the competent authorities when required. 

**URL:** https://dnsbl.evilnet.org

**Contact:** https://dnsbl.evilnet.org/contact

**Request Removal:** https://dnsbl.evilnet.org/request-removal

**IP Search:** https://dnsbl.evilnet.org/ip-search

**In what CLASS my ipaddress can be add on EvilNet DNSBL:**

```
127.0.0.[3] = Join/Part
127.0.0.[5] = Compromised HOST/IP
127.0.0.[6] = IRC Spam Drone
127.0.0.[7] = DDoS Drone
127.0.0.[8] = Open Proxy/HTTP Proxy
127.0.0.[10] = Abused VPN Services
127.0.0.[17] = Auto determined botnet IPs (Default)
127.0.0.[18] = Compromised DNS/MX type hostname

```

# EvilNET-API-Doc
EvilNET API Documentation

`API URL:` https://api.evilnet.org/

`API RBL:` rbl/ip/

### How to Use

`URL FAST Search:` https://api.evilnet.org/rbl/ip/

**NOTE:** Need a real IP Address to add on the url.

`Example:` https://api.evilnet.org/rbl/ip/Your-IPAddress-Here

`Body Result Template:` 

```
    {
        ipaddress: " ",
        dateadded: " ",
        reportedby: " ",
        iptype: " ",
        attacknotes: " ",
        email: " ",
        location: " ",
        id: " "
    }
```


### This app is running on NodeJS
#### You can make a request with some modules

### NodeJS Request.

```
// Import Request from Request. This use the new module system call.
import request  from 'request';
request({
    url: "https://api.evilnet.org/rbl/ip/Your-IPAddress-Here",
    json: true
}, (error, response, body) => {
    // Print the JSON for the API IP request.
    console.log(body);
    // Print the response status code if a response was received.
    console.log('statusCode:', response && response.statusCode);  
    // Print the error if one occurred.
    console.error('error:', error); 
});

```

### NodeJS Axios.

```
      // Import Axios from Axios. This use the new module system call.
      import axios from 'axios';
      // Get API Url Fetch in axios module.
      axios.get("https://api.evilnet.org/rbl/ip/Your-IPAddress-Here")
      // Show results only with data info.
      .then((result) => {
          console.log(result.data);
      })
      // IF catch a error print the result message.
      .catch((err) => {
          console.log(err);
      })
```
#### **NOTE:** Remember we are using the new import method from NodeJS.
#### Need to add on package.json ` "type": "module", ` so you can import like a module.

#### How to Install Axion
#### Package manager
#### Using npm:

```
$ npm install axios
```

#### Using bower:

```
$ bower install axios
```

#### Using yarn:
```
$ yarn add axios
```

#### Using pnpm:
```
$ pnpm add axios
```
#### Check Axios DOC: `https://www.npmjs.com/package/axios`

#### How to install Request

```
npm i request
```
#### Check Request DOC: `https://www.npmjs.com/package/request`

#### **NOTE:** Request using old method to call a import.
#### If you going to use like a module need to to the new import.

### Old Style Call Import
```
const request = require('request');
```

### NodeJS HTTPS.

```
// Import Https from Https. This use the new module system call.
import https from 'https';
// Get API info with HTTPS
https.get('https://api.evilnet.org/rbl/ip/Your-IPAddress-HERE', (response) => {
    // Create a data
    let data = '';
    // Chunk the date in to a chunker
    response.on('data', (chunk) => {
       data += chunk; 
    });
    // Show data chunk on the https
    response.on('end', () => {
        console.log(data);
    });
})
// Show Error message.
.on('error', (error) => {
    console.log(error);
})
```
### How to install Https nodeJS module.
`npm i https`

**Check documentation about HTTPS nodeJS Module:** https://www.npmjs.com/package/https

## PHP 8 API JSON Decode.

```
<?php
	$apiRBL = 'https://api.evilnet.org/rbl/ip/Your-IPAddress-Here';
	$json = file_get_contents($apiRBL);
	$DNSBL = json_decode($json);

		echo "ID: " . $DNSBL->id . "\n"; 
		echo "IP Address: " .  $DNSBL->ipaddress . "\n";
		echo "IP Type: " .  $DNSBL->iptype . "\n";
		echo "Attack Notes: " .  $DNSBL->attacknotes . "\n";
		echo "Date Added: " .  $DNSBL->dateadded . "\n";
		echo "Location: " .  $DNSBL->location . "\n";
		echo "Reported by: " .  $DNSBL->reportedby . "\n";
		echo "Email: " .  $DNSBL->email . "\n";
?>

```
**NOTE:** This php code, get info from api and print in terminal.
You can use this code in your website or in any place you want to show info from the RBL API.

**PHP Json Decode - TEMPLATE Looks like**

```
ID: 
IP Address: 
IP Type: 
Attack Notes: 
Date Added: 
Location: 
Reported by: 
Email: 

```
**NOTE:** You can print only the part you need. Check DOC about JSON Decode.

**URL:** `https://www.php.net/manual/en/function.json-decode.php`

## PHP 8 API cURL.

```
<?php
	//API URL Configuration.
	$apiRBL = "https://api.evilnet.org/rbl/ip/Your-IPAddress-Here";
	// Execute apiRBL
	$DNSBL = curl_init($apiRBL);
	curl_setopt($DNSBL, CURLOPT_RETURNTRANSFER, 1);
	curl_setopt($DNSBL, CURLOPT_SSL_VERIFYHOST, 0);
	curl_setopt($DNSBL, CURLOPT_SSL_VERIFYPEER, 0);
	//execute the session
	$dnsbl_response = curl_exec($DNSBL);
	//finish off the session
	curl_close($DNSBL);
	$api_result = json_decode($dnsbl_response, true);
	// Print the results from API
	print_r($api_result);
?>

```
**PHP-cURL - TEMPLATE Looks like**

```
Array
(
    [ipaddress] => 
    [dateadded] => 
    [reportedby] => 
    [iptype] => 
    [attacknotes] => 
    [email] =>
    [location] => 
    [id] => 
)

```

**NOTE:** You can print only the part you need. Check DOC about PHP-cURL.
Make sure you got php-curl install in  your server.

**URL:** `https://www.php.net/manual/es/book.curl.php`
