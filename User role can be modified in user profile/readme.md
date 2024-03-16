## Lab Description:

<img width="828" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/73ffddc0-aa37-41bc-9c5c-1e852326b46c">

## Solution:

Enter the credentials which are given for testing which is wiener:peter & click LOGIN button, the captured request is as follows

<img width="1049" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2aefb975-6105-405b-a313-24ff3e23c688">

Till now we didn't see any suspicious cookie values being sent from our client

Lets move on & try to update our email.

<img width="1141" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/da1bfc25-812e-4030-b9bf-4a85bbc0dece">


![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5c3598dd-15ff-44de-b1dc-a2e9d25577e6)

Observe that we have a roleid=1 in the JSON response.

So add the value roleid=2 in the JSON request & see what is the response in browser

<img width="1031" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/95e92652-d2bd-4d77-a096-c83f8bc9e230">

We have a 302 redirect, click follow redirection.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2fde3e5d-7cbd-41d4-8edf-6595e89c8505">

Now we can see the link to Admin Panel in the browser.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8da88391-cfed-4515-9631-12086937d51f">

Now click on admin panel & delete the carlos user to solve the lab.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4a772388-3d60-47c4-9168-a74b8ea2d71a">



