## Lab Descriptions:


<img width="880" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0a35c755-f843-4fc1-bdf1-36349527cb65">


## Solution:

If an application requires that the user-supplied filename must start with the expected base folder, such as /var/www/images, then it might be possible to include the required base folder followed by suitable traversal sequences.

For example:


<img width="1435" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8b5f9e3d-91bb-4033-8953-157ec8465965">

When we just give ../../../etc/passwd payload in the filename= parameter , we get a 400 Bad Reques in return. This is because the server expects the filename must start with an expected base folder which is /var/www/images.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/23306f30-f1bb-4a7f-809a-97a794f4935d">

So , we need to send a payload to retreive the /etc/passwd file where the payload starts with /var/www/images.

When we give /var/www/images/../../../etc/passwd as payload to filename parameter we can retreive the contents of the file.

<img width="1431" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ce58804b-1cc6-4361-9f9e-4ade37b2eeab">

## Result:

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a9ab75c2-654b-42d1-8b39-da63968fef22">

