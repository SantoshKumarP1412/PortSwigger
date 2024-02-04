## Lab Description:

<img width="712" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/fb4ad7e5-5a7e-480e-9aae-8b276d8f4c14">


## Solution:

Cause a 10 sec delay in response -
The request looks like this


<img width="590" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5d9c27d3-a3ed-445c-82f1-0d7d062c88a0">

SLEEP command differs for each type of databse, here we find it by trial & error method that it is a POSTgreSQL database

<img width="897" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/84158c6f-c12a-47a1-bc59-0050be2e71e2">

To do this we can use the following payload

```TrackingId=x'||pg_sleep(10)--```

<img width="1205" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c61c4485-c0b7-498e-8293-05e80bd4af89">

We get a response after 10 sec which confirms the SQL injection vulnerability.

<img width="1218" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0bb5560f-7e13-4c0b-ab2d-0b3887b28019">





