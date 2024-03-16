## Lab Description:

<img width="934" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d69c2187-1673-42a2-8e06-5134ae41c7bb">


## Solution:

The account page that contains the current user's existing password, prefilled in a masked input. So lets login as wiener to see what the account page has.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/eec21d68-dcb4-4df0-b0d7-6290ad80e9bb">

We can see there is a pre filled password in the password field. We can't see the password in plaintext but we can try reloading the page / view source-code to see what the password is.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/82fbc3d4-11e5-47d1-a7de-231aae7c0b2b">

So the password is prefilled with the password of the user winer which we logged in.

Now if we click on the My account link again after logging in , the page reloads where it sends a request as below.
<img width="568" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3ebfcaeb-bfe8-4fd4-a578-c89e9a139e16">


Change the parameter ?id=wiener to ?id=administrator.

Thus we have sucessfully exploited it as it leaked the admin's password in the response.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/be77f339-584d-42ac-9e2e-1b8c7fba0caf">

Now we can login as admin & delete user carlos to solve the lab.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0d238ff6-4ff4-46a4-ae7d-6a009a138603">

