## CSRF where token validation depends on request method

<img width="896" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/48fd0d6b-ef33-4012-922f-3d0fcbd2152a">

## Solutions:

<img width="1155" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0f4a5e0a-a6a0-4a87-9d74-d5c3e4229295">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/650e9b53-0a0e-42b1-acb6-c8fe0c11d839">


Change request method to Get method from Post Method


<img width="1264" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1fd15caa-47f5-4cce-8a1d-a4ef4c6a9b44">

<img width="1131" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/290caa86-ef63-48d0-a4be-a8f709e0d8f0">

we have an extra parameter as csrf token that we can remove and make an CSRF as an POC

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/fdc8798d-6479-4c15-846e-0ec02357bdb3">

This is an html script which has to be hosted on exploited server


<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/26f76fd0-ab15-4b38-8ace-d8d6dd1d6313">

Now we have to click on Deliver exploit to victim

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2d8c03e4-27f9-4328-94c5-bff37bab8dc6">

