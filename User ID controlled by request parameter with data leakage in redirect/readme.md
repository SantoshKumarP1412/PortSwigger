## Lab Description:

<img width="952" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/01d63e93-0e53-41a2-9f53-a0a4b3261bf8">

## Solution:

Clicking on My Account takes us to the login page where we can login as wiener useing the credentials wiener:peter.

We get the account page which displays wiener's API key - 5Xwv27q2IJey2uG7CpOJ94FfFbyREaXn

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6d4b126a-d7e5-4dc9-8151-fbcf0b08ae85">

When we click on My account again, the browser sends a request which contains ?id=wiener

Send the request to repeater tab. Change the value to ?id=carlos and observe the response.

We get a 302 Redirect response back .

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/163e4284-6763-446e-ab22-1530fe0f44c7">

Here the API key of Carlos is leaked in the redirect response.\

<img width="457" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4330e051-bf2d-4c0e-9f3e-7ea522ceb462">

Submit the key and the lab is solved.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/63a62e88-e709-44a3-afa4-651ff941c6dd">

