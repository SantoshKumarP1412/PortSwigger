## Lab Description:

<img width="891" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b69275bb-9718-47ba-b025-0ea3347dac14">

## Solutions:

Capture the request:
We can perform SQL injection attacks using any controllable input that is processed as a SQL query by the application. For example, some websites take input in JSON or XML format and use this to query the database.

These different formats may even provide alternative ways for you to obfuscate attacks that are otherwise blocked due to WAFs and other defense mechanisms. Weak implementations often just look for common SQL injection keywords within the request, so you may be able to bypass these filters by simply encoding or escaping characters in the prohibited keywords. For example, the following XML-based SQL injection uses an XML escape sequence to encode the S character in SELECT:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1b367f4e-2066-410b-8e56-90613c08e832">

There are 2 xml tags where we can inject our sql injection payload ie productID & StoreId.

When testing sql injection query in productID, we get a response like this

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d1819fb0-1603-4072-bc19-ef155f5ed6ac">

Both show the same 403 Forbidden error

Why is it getting blocked?

A web application firewall (WAF) will block requests that contain obvious signs of a SQL injection attack. You'll need to find a way to obfuscate your malicious query to bypass this filter. We recommend using the Hackvertor extension to do this. 
So we need to bypas WAF and execute our sql payload.


## Bypass WAF -
We need to Obfuscate out xml payload inorder to bypass WAF. As per lab description we'll use Hackvertor for this

Hackvertor is a tag-based conversion tool that supports various escapes and encodings including HTML5 entities, hex, octal, unicode, url encoding etc. It uses XML-like tags to specify the type of encoding/conversion used.

NOw select the payload -> Right click -> Extensions -> Hackvertor -> Encode -> Hex entities

<img width="1434" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/057551ec-78eb-465c-88ac-39f552cbba11">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a727c065-970e-4f42-b46f-da8af2798ff1">

So we can now confirm that storeID parameter is indeed vulnerable & we bypassed the WAF by encoding our payload with hex entities.

ProductID parameter doesn't seem to be vulnerable since it didn't return NULL value in response
<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/416373fa-16b9-4572-8fc1-7d4c185b0200">

Craft payload -
Our payload to retrieve the admin user's credentials from users table,

UNION SELECT username || '~' || password FROM users
After encoding it with hex entities by using hackvertor,

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c02ec241-8706-4228-920a-3e07e23fe9e2">

Result:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6f422da6-0a62-4ae9-a57b-022692a34d55">
