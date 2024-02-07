## Lab Description:

<img width="854" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9f16518d-682f-40fb-91c4-983eea91ffae">

## Solution:

When we load the page, we get several items with its images, a request is being made to retreive the images from the server.

Send the request to Repeater.

Now in the filename parameter we have to test each payload by traversing back to find the ```/etc/passwd``` file.

When we give the payload as ```filename=../../../etc/passwd``` , we get the contents of /etc/passwd

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/03929414-f5fb-4a9a-a49a-4a8bb90cac21">

Result:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/779f89bd-5dd3-45cd-83b1-ffeb4d04e54c">


