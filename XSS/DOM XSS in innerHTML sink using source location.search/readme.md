## DOM XSS in innerHTML sink using source location.search

<img width="880" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ea371c24-4a38-45f1-aa5b-165cd2b76431">


## Solution

The lab application is a blog website with search functionality.

First try entering the following simple XSS payload to trigger an alert!

``"><script>alert(1)</script>``

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4cdb1197-da1c-44ab-98fd-ab13c52aa206">

But no pop came.

The innerHTML sink doesn't accept script elements on any modern browser.

<img width="572" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/53f78b1a-7b31-4f5b-913a-04bd302e7412">


what ever query we are typing stored inside span becuse of innerhtml for bypassing it we will use an alternative elements like img or iframe. Event handlers such as onload and onerror can be used in conjunction with these elements.

XSS payload to trigger an alert!

``<img src=1 onerror=alert()>``

The value of the src = 1 attribute is invalid and throws an error. This triggers the onerror event handler, which then calls the alert() function. As a result, the payload is executed whenever the user's browser attempts to load the page containing your malicious post.

This raises the alert box.

<img width="1369" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e4e1512a-84b2-46d9-beed-5efcdf3e4db9">

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/18c80bc8-cee9-4b67-89ee-bed92cf31664">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/748dacfd-c3f0-4cd7-8871-e212ec42d6a5">


