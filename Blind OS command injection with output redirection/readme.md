## Lab Description:

<img width="898" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e36d94a9-cd3d-46b0-a881-946fca55655a">

## Solution:

Submitting the feedback form , the request looks like this

As we know, the email parameter is vulnerable , we give the payload  & whoami > /var/www/images/op.txt # (URL-encode before sending)

<img width="1224" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5c8465e4-0898-47e4-9879-51702084fd68">

We get a successful response


<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/79aa43dd-f69e-4a0c-891b-f1cb3ecdcd9f">


<img width="1432" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e093a648-e3db-4180-97c0-ac89032700cb">

Result

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/67aa276e-8b70-4ef5-be86-d414437e867b">


