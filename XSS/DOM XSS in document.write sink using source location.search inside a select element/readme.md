## DOM XSS in document.write sink using source location.search inside a select element

## Solution:

The lab application is again the shop website containing the stock check feature. This time, the selection box for it is created dynamically by client side JavaScript. The defining feature that requires this is that if a store ID is provided in the URL, the store is pre-selected. For example, adding &storeId=paris to the URL will put Milan in first place of the list and selects it:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f733bd6f-3a73-45e9-922a-9ecb15dd4a8b)

This is done by this Java script-

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/368aaeda-2c9b-4543-a07a-e8e964711816)


HTML looks like this-

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0174f57a-06c6-49b0-8390-90b1742a3c92)

I can not directly add some JavaScript in the text of the option tag. But I can complete the tags and put script content outside of the scope of the option.

Payload to script to get the content outside

``&storeId=Paris</option>we can script here ``

The resulting HTML looks like this-

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d30f3151-fe9f-4bc7-8e3e-13125591585f)

The location of the we can script here is just a right spot for adding a script.

Modifying the URL to use-

The Payload is-

``&storeId=Paris</option><script>alert(1)</script>``

This raises the alert box.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/92604780-bb43-4822-b6b5-19ae38f30d60)


The resulting HTML looks like this-

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a1f20766-b073-4259-9337-f3365c83b7b9)


![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/fd7cda1f-82da-4031-aaa1-2d2d85413740)
