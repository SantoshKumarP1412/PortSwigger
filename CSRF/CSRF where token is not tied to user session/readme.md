## CSRF where token is not tied to user session

<img width="891" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1b4a6349-4dc4-4554-bd8f-9fff8f5ea811">

## Solutions:

When we are logging in the web application and updating email as wiener user

<img width="1290" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d33857c3-52a9-4754-a7d3-10de6c6d1014">

When logging as carlos user

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/35555f59-1ca5-4ea0-b77d-7f6dd6add0b4">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/73e44353-44bf-498d-807e-b7702bc3f4f7">

So by swapping csrf token of two users we can easily change email address.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0346ae3b-6deb-41c3-a498-84d851f121db">

Hence it is not tied to any specific user session

we have to reload the page of carlos user and get csrf token

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/dba42f74-8214-4f5b-984b-6935249b796d">
