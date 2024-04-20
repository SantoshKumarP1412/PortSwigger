## CSRF with broken Referer validation

<img width="918" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3011689a-abf9-46ee-a1d5-84b4a58a740d">

Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3c8cdfe0-e80b-4a7e-adb8-b212247da161">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/7dc474d8-0c82-4031-9134-b82bb4b8eb8f">

Copy the original domain of your lab instance and append it to the Referer header in the form of a query string. The result should look something like this:

Referer: https://arbitrary-incorrect-domain.net?0a84007a037bd49681013eee007a009d.web-security-academy.net

Send the request and observe that it is now accepted. The website seems to accept any Referer header as long as it contains the expected domain somewhere in the string.

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/7d7fdd6e-e7e0-4f2b-9213-9b700a115b1d">

Create a CSRF proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab and host it on the exploit server. Edit the JavaScript so that the third argument of the history.pushState() function includes a query string with your lab instance URL as follows:

history.pushState("", "", "/?0a84007a037bd49681013eee007a009d.web-security-academy.net")

This will cause the Referer header in the generated request to contain the URL of the target site in the query string, just like we tested earlier.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/76a3e65d-90df-4ef8-953d-de0e37e60c73">

This is because many browsers now strip the query string from the Referer header by default as a security measure. To override this behavior and ensure that the full URL is included in the request, go back to the exploit server and add the following header to the "Head" section:

Referrer-Policy: unsafe-url

Note that unlike the normal Referer header, the word "referrer" must be spelled correctly in this case.
<img width="1424" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6fb0d24b-8823-420d-b396-cf0675324cb5">
