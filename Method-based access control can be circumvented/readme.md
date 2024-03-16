## Lab Description:

<img width="906" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4de5cd34-03bf-4682-915e-ca81ca594dce">

## Solution:

This lab provides the administrator credentials to analyse the workflow of granting and revoking administrative permissions to users. It basically is just a form to select a user and using an Upgrade or Downgrade button:

In the background, POST requests are sent to /admin-roles.

Nowusing the credentials administrator:admin we have logged in as administrator.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f97f2297-89ce-4773-a665-728e829c909c">

We see that there is a link to admin panel. Clicking on admin panel takes us to this page where we can upgrade or downgrade the privileges of a user.

Click on any action && capture the request and send it top repeater as it may come handy later.

<img width="570" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a453708b-bcb5-4447-86e8-2363096ec6d5">

We can see that in this POST request we have a parameter called username=carlos & action=upgrade

The above reqest upgrades the privileges of carlos user.

Now Log out of admin user and try loggin in as wiener

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/cac646ff-8911-4d38-9081-9a5d93ddd991">

Reload the page & capture the request & send it to repeater.

Our goal is to exploit the flawed access controls to promote ourself (wiener) to become an administrator.

So we can try to perform the role changing action as wiener by pasting the cookie value of wiener in the request made by admin to change the privileges !

Cookie of admin - 6siUFNzqgvZGuGPXfxu7lFIiDXgNKdF5 Cookie of wiener - T0lAJAlHhdoNt8LZIK7VB45FxcSyawzE

So we change the cookie value of admin with wiener & send the request, we get the response as 401 - Unauthorized

Request -
<img width="563" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5bf07e5e-7810-43cd-902a-ca13683c6a0d">

weiner cookies 62rMOnwe2ggXMYNdQSGkaZxLqr82fqql

Since this lab is based on Method-Based-Access control bypass, we can try to change the request from POST to GET. We can do this by Right click on request -> Click Change request method option.

Now it changes to a GET request,

Solved

<img width="1426" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f8b302cd-9a1b-4333-a9d7-e57dee70b280">


