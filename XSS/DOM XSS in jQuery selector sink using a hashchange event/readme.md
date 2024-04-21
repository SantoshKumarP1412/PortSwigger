## DOM XSS in jQuery selector sink using a hashchange event

<img width="865" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/139bcec8-6a0f-4ccf-be41-97f9fea872df">

## Solution:

The first step is to analyse the web application. An interesting script can be found at the bottom of the page:

A quick check in some online documentation shows that the script is used to scroll to a post indicated by the fragment part of the URL. Using the title of a post after a #, the browser scrolls to the post.

entering ``It's All in the Game - Football for Dummies after #``

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1e58bc9e-4bd1-434f-9e9e-2300d2a90208">



<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5e05c9de-fba7-4b57-9cfc-a845ba0b4c7e">

<img width="988" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/270cfe84-c848-4e2e-a897-ca8af9d2989c">

