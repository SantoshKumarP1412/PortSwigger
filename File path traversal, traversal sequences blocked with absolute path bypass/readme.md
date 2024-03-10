## Lab Description:

<img width="894" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/19577756-9b5f-48c8-9922-ce7e20603546">

## Solution:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/03520bcd-518b-492d-b830-0359c8697a37">

In this lab, the application blocks traversal sequences but treats the supplied filename as being relative to a default working directory, so we 'll use an absolute path from the filesystem root, such as filename=/etc/passwd, to directly reference a file without using any traversal sequences.

We get the /etc/passwd file from the response.

<img width="1237" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ba49597e-56be-4c44-aff6-1a2890991bfa">

## Result:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/12ba8867-7df5-426a-97a9-1d5831703564">
