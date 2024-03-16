## Lab Description:

<img width="918" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6cc3c7fd-57ee-410c-bb22-a39080ba7f20">

## Solution:

Admin user -
First can familiarize yourself with the admin panel by logging in using the credentials administrator:admin.

Then we can play around with the requests by loggin in as wiener & exploiting the flaw in the multistep process.


Once logged in , we can go to admin panel & modify other user's privileges.

We need to upgrade wiener as admin by flawed multistep process, so lets now poke around with carlos.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b399b98a-e678-4b7f-93dd-0aa7da2e0657">

Cookies id of wiener

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ca1f19cb-9f68-4af1-a621-26413b6ce861">
Cookie of admin - ZpyoZWrt5YplfvsXMA2ayoFLn3iAX9GN Cookie of wiener - DVWBhHWy8qAAnzPIfHLrhQmuEYDR4shV

Let send the non admin request with the admin's session cookie.

If we try to upgrade ourself(wiener) by changing the cookie value of admin to non admin in the request of first step , we get 401 - UNAUTHORIZED
<img width="641" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0a12a3fb-d0dd-4c84-99de-a4ce6e30a8cd">

Solved

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8f098ec4-cdbe-4d3b-b76d-7451f319b9ba">

