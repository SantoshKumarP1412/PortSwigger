##  DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

## Solution

This lab mentions AngularJS expressions. I never used it before so a quick google search leads to the respective documentaion on the angular website.

AngularJS expressions are executed in HTML sections inside of nodes containing theng-app attribute. Fortunately, the full HTML body of the page is set as valid scope:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/573e6b98-f9f8-494f-a0c7-c7bf9239ce77)


The most trivial example given at the documentation linked above is a simple addition with {{1+2}}. So using foobar{{1+2}} as search term, the search term is displayed as:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a7a3cb05-7573-4577-9b32-184d5db30ea3)

This confirms the execution of the expression. The next step is to find a possibility to inject script code.

payload to trigger an alert!

```{{$on.constructor('alert(1)')()}}```

PortSwigger This page also contains example payloads that can be used to inject Javascript into Angular.

This raises the alert box-

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d9e4acde-1359-4fe6-b8e0-231098a3d11c)

<img width="1436" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6f991f07-c06d-41ad-b571-645426b571e9">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/14054472-3dea-4e54-8eed-9a7b0a33bf7a">

