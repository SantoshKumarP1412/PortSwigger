## CSRF where Referer validation depends on header being present

<img width="886" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f1fbda24-069b-4548-8af2-901a60b36dc6">


Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/edc4243a-c699-4a6c-977a-6626d2f3bdaa">


when viewing the exploit it will show as invalid Referer header.

Then Delete the Referer header entirely and observe that the request is now accepted.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f10f8f9c-07f6-419f-88e4-5c0ccb891aa9">

Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab. Include the following HTML to suppress the Referer header:

<meta name="referrer" content="no-referrer">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d4c1a21c-58f4-4428-8274-e57943df60df">

