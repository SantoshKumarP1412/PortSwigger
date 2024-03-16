## Lab Description:

<img width="857" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d17c4b62-8ef7-4d99-a7db-bd75316def62">

## Solution:

When the lab website loads, we straighaway see the Admin panel link present.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/88b1dfd8-3eaf-4eed-987d-c2958b101a3e">

When we click it we get Access Denied.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/80f28fa4-bf58-477c-ad26-f6bee485736c">

We capture the request in burp .It looks like

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c6f2a891-ac25-4e30-87ee-206208a36fc5">

The hint given in the lab description helps us to bypass this ,

Hint - The back-end application is built on a framework that supports the X-Original-URL header.

Some application frameworks support various non-standard HTTP headers that can be used to override the URL in the original request, such as X-Original-URL and X-Rewrite-URL. If a web site uses rigorous front-end controls to restrict access based on URL, but the application allows the URL to be overridden via a request header, then it might be possible to bypass the access controls using a request like the following:


POST / HTTP/1.1
X-Original-URL: /admin/deleteUser

Top bypass this 403, we should remove the /admin which is with the GET method in the URI in the request & add the X-Original-Url : /admin to the body of the request.

Common mistake is that we add the endpoint both in the X-Original-Url & also at the GET method.

<img width="1434" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/561e6401-ae9c-43e8-95c8-11caadb0d4a1">

Thus we got the admin panel.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8564e1ed-9526-4f35-8c88-29785e594db5">

If we click on the link to delete user carlos, we again get access-denied.

So we have to add the custom header in this request too !

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f22a68c6-a53a-43fc-a018-370afd0b71a9">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8a3fb775-0a20-4e88-8aff-282bdcb0ebba">

