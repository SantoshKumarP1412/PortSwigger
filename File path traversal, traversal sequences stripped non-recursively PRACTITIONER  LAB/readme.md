## Lab Description:

<img width="966" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2e961429-27a8-4fc1-8152-4e3d5a0db45c">

## Solution:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f733b32c-6af8-4648-b1c3-52eb1e5f1da1">

When we give ../etc/passwd , the web application strips the ../ so the user input is interpreted as etc/passwd.

To bypass this we need to give nested traversal sequences like ....//etc/passwd so that even if the server strips ../ so the resulting query which will be processed by the server will be ../etc/passwd.

First we give this i/p - ....//....//etc/passwd

We get this response containing 400 Bad Request.
Next when we try this payload - ....//....//....//etc/passwd , we get the contents of the file.

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0108a60a-6043-41c7-bb17-241fb749e462">


## Result:

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d34f24a8-33aa-43bd-b273-036b99f11022">
