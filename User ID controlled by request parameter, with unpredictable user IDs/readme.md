## Lab Description:

<img width="880" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e70f7f49-e0d9-404d-b876-79af9a5bcdf0">


## Solution:

Click on My Account , it takes us to login page. Use the credentials wiener:peter to login.

<img width="1278" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1b41e9a4-3ef9-4203-97de-cb5c8360f708">

Once we login, we can see the API key of wiener.

Click on My Account & capture the request.

We have the GUID of wiener in the request. We need to somehow find the GUID of carlos to get his API key.

For that , click on the home page and browse through all the blog posts by carlos, Click on his username

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9ea29970-03ab-4b50-8e40-54f6c36e9bc9">

Now we got the GUID of carlos - dcf02547-1af6-46ab-8445-e466163a1421



<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8cfa586f-8228-472a-8ae6-a754603cd1ea">

Now in the My Account page , click on the link , capture the request and modify the GUID of wiener with carlos to get the API key.

weiner GUID

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2b76c021-5aad-466c-ba2f-1431d319f484">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8b21bb13-0ba1-4110-b4e9-d2ecc71a5ab1">

Solved

<img width="1418" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3d6095d5-e24b-44bd-8c18-6bb6c900dd1a">



