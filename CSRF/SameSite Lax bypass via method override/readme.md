## SameSite Lax bypass via method override

<img width="913" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a27da8d4-f6e9-4b94-b8bb-d526fedc844f">


## Solutions:

Go to My-Account and Log In to the account with the above credentials and change your email address.



Send the POST /my-account/change-email request to Burp Repeater.And Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens so may be vulnerable to CSRF if you can bypass the SameSite cookie restrictions.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1442dbc5-e210-45e4-b471-1728bacdb9c4">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6b9e7f2c-d2c0-4db7-af52-5b4136bb7222">


Try overriding the method by adding the _method parameter to the query string:

/my-account/change-email?email=foo%40web-security-academy.net&_method=POST
Send the request. Observe that this has been accepted by the server.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9fdbaeb4-47bd-442a-ab5c-70982ba9712d">

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1a5ad518-bbe7-4b67-9773-64823a34c1de">
