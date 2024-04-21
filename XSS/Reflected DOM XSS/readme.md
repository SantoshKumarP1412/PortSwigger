## Reflected DOM XSS

## Solution:

In Burp Suite, go to the Proxy tool caputer the request when typing cyber

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0562737f-1efc-4d0e-be38-497737a8bbce)


Notice that the string is reflected in a JSON response called search-results.

From the Site Map, open the searchResults.js file and notice that the JSON response is used with an eval() function call.

<img width="1434" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/460c5f26-2ac0-4bd7-a9a5-54d8c90adb8f">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/71cf679c-fa97-42e8-90a9-f27599ff2b4c">

Payload-

Now we will make out payload by -alert() instead of man we are using - because + usually url encoded.

``\"-alert(1)}//``


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c61532b6-31fc-41ad-84b1-d4136102a213">

Now go and search the payload and it will trigger an alert!.

<img width="1429" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/00db0161-aaf9-4577-9dec-74f5ad1e598b">

