## Stored XSS into anchor href attribute with double quotes HTML-encoded

## Solution:

We have a functionality to post comments.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/64c796c4-da95-4eeb-be88-5c2fa984a9c3">



We can use the following XSS payload in the comment field to perform a stored Xss attack.

```javascript:alert()```

<img width="802" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/304b0eab-2ed6-44b8-b1e6-0707e3618111">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8640cda0-2338-42c1-ae2a-708693e2d838">


