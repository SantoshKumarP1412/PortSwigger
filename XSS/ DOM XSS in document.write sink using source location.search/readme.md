##  DOM XSS in document.write sink using source location.search

<img width="884" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/bf72f301-d29e-4db9-b85b-51865dbf8010">

## Solution:

We straightaway see a search functionality.

After performing a search cyber, the search term is included on the result page.

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/062e4f06-557c-4dfa-a65b-93174af7ed2f">

Looking at the page source, the search term displayed is properly encoded. However, it also shows that a javascript takes the search term out of the URL and writes it into an img-tag for some type of tracking. it only show the jave code not what really is happend there.

<img width="505" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4efa0f2c-284c-458e-b0e9-83d41682c7cb">

Using the browser tools, I can inspect the resulting HTML. It is visible that my search term is embedded without any apparent safeguards:

<img width="502" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0eaca375-207e-47a3-bc00-cc4a3c719055">

Enter the following simple XSS payload to trigger an alert!

``">cyber<script>alert(1)</script>``

Break out of the img attribute by searching

it trigger an alert.

<img width="1385" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6365ef80-d8dc-40c4-9e25-710420f8c9b4">

<img width="955" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/51d7084d-8bfb-4d81-babe-f260db558ef7">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/adc0b723-9fd1-429e-9d88-e82f0d4b419c">


