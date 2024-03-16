## Lab Description:

<img width="865" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/77c6a8a4-eb11-4cf5-a191-69c68c59e97f">

## Solution:

When ther lab loads , we see the usual shopping website. Clicking on My account takes us to a login page.

We enter the credentials which is given in the lab description - wiener:peter

When we login we get to see the API key of wiener - PXd9QBEisO7D1jZmH7s5QgwZYXd8je09

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ed0bee97-f90e-442c-9a0c-8960603aa487">

To solve the lab , we need to retreive the API key of carlos user.

When we click on My Account after loggin in as wiener, a request is sent like this

<img width="572" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9577cb34-4efb-4707-bfc6-e521bc7a23ee">

It contains ?id=wiener parameter.

Change the value to carlos , we get the API key of carlos and thus solved the lab

<img width="1144" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/7879589a-8efd-4525-a92a-e905d430c246">

solved
<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d9db5022-d7e7-4621-af7a-470749a89e5f">


