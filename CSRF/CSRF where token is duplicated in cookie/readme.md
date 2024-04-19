## CSRF where token is duplicated in cookie

<img width="935" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ddc89bbf-facf-4bb8-99a3-2b0cfab75198">

## Solutions:



Send the request to Burp Repeater and observe that the value of the csrf body parameter is simply being validated by comparing it with the csrf cookie.

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/fa2297c4-8f5a-4394-9ec5-4ff4bb1137c8">

As soon as an adversary is able to set cookie values, the CSRF-protection can be circumvented entirely.The token may or may not require the proper format, so I just try it out with an arbitrary short value:

Create a URL that uses this vulnerability to inject a fake csrf cookie into the victim's browser:


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/964eb9af-76dd-4874-9c86-8edcf7e1b824">

![Uploading image.png…]()

