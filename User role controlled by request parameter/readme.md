## Lab Description:

<img width="823" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8332cf2d-1c11-4f72-9062-f8b8fe8f7bd3">

## Solution:

We have our login page,

<img width="1149" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/764f5112-b192-44ae-88eb-1cd544c5372a">

In the lab description , it is given that the admin page is at /admin. Lets try visiting that page.

<img width="1142" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c06aa0f2-55ed-4344-971e-19af8e7a6810">

It says we can view only if we are admin!

We have a login credential wiener:peter .Lets try logging in and see what requests & responses being made.

Once we hit login after entering username and password, it sends a POST request like this,

<img width="549" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b0fc8880-d8e7-4f59-8bbd-565f7649f901">

Then a GET request is made to retreive the /myaccount page .

<img width="563" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/73a20c18-fc07-4527-a76a-90611a0915dd">

Here we have an interesting cookie - Admin=false.

The reponse looks like this ,

<img width="585" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f66bb6d0-2d38-48fc-bb6b-16d3dae6102e">

We are logged in as wiener

## What happens if we change the cookie value to Admin=true ?

We modify all the requests where the cookie is set to Admin=false to Admin=true`

POST req to /login endpoint

<img width="1165" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/295e2516-097e-44d9-9f79-94ff6024e71e">

GET req to /myaccount endpoint

<img width="1159" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0f51e017-978c-4dcd-aad9-a801867f0073">



GET req to /admin endpoint
After getting the myaccount page, we click the Admin panel link, the request sent is modified as follows

<img width="1162" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b4787750-7764-459d-84e2-759c7b9f6796">

Atlast, we get the admin panel .


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ef117186-7ac4-4b44-b04b-fea05c269c8e">

We have sucessfully solved the lab.

<img width="1394" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/cd290844-393e-4e23-8707-2d5a6f0a574d">

