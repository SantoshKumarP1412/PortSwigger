## Lab Description:

<img width="917" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/870995c4-567c-4a37-bf1f-7ff1ad48c8dd">

## Solutions:

The request which loads images loooks like ,


In this lab , the server strips all the directory traversal sequences ../ & also ..%2F..%2F..%2F(doule encoding), so to bypass this we can use triple encoding.

So to bypass this we use triple encoded version of ../../../etc/passwd as ..%252F..%252F..%252Fetc%252Fpasswd as payload.

Now we got the response back containing the response of the file.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8b5a77d9-a656-4c05-9ee9-604619ac2cad">

## Result:

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b69b0db1-e434-492b-a5f0-a2c7d6d0413a">
