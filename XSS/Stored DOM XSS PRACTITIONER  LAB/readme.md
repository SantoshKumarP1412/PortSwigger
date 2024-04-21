## Stored DOM XSS


## Solution

We have a functionality to post comments.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/45e3065d-9c54-484f-bd5e-b4473a8fac1a">


First i used normal alert payload for stred xss.

``<script>alert()</script>``

alert did not came.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e83b6d2a-977c-484d-b11e-2f272e2eaa7f)

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b31981a6-d12c-4fcd-a0de-3f7e075e4213">

HTML code -

So the natural next step is to check that JavaScript. Some things become obvious:

The content of the elements are added as innerHTML, which is vulnerable to injections (innerText would be better here)

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/72a72427-04f4-4e03-aa5d-25b2d7df01e4)


we need come out of the <p> script </p>. for that we will use <> how out of that our scrpit will have this in front.

Payload.

```<><img src=1 onerror=alert()>```

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/914d83be-9565-4fbd-98b8-05d675bf4958">

