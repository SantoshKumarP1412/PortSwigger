## Reflected XSS into a JavaScript string with angle brackets HTML encoded

## Solution:

Submit a random string in the search box.Observe that the random string has been reflected inside a JavaScript string.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0d74cf46-312c-45ba-9a4b-56d8a20e266b)


Replace your input with the following payload to break out of the JavaScript string and inject an alert:

``'-alert(1)-'``

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/169066b6-fb97-48b8-9217-e0b710b6806a)

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/00c9ea46-88ce-4526-987d-e8b17144a543">
