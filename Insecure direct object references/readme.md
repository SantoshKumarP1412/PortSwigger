## Lab Description:

<img width="876" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/01eb0e72-3523-474a-bd21-e8353e59dc0f">

## Solution:

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6aaf15dd-b89e-41ef-85e5-ffd4d67d0d79">

The lab page contains a Live chat link which allows us to send messages and also view transcripts,

Opening the transcript

<img width="945" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/538c6c30-bee4-4ec0-96c2-f9fe8c53b8e5">

Notice that The transcript downloaded was 2.txt and why not 1.txt?. Maybe there was previous chats which contains carlos's password

Lets repeat the same process but capture the request when clicking on transcript button.

The browser sends 2 request,

**POST request to /download-transcript **

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5b7b551b-9180-4028-b734-8883e6f168cd">

GET request to /download-transcript which downloads the file to our system -

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6c34ebcc-4246-4fb1-a3ff-50085cd543b2">

It retreives a static file 3.txt , lets change it to 1.txt.

As we guessed, the first chat 1.txt contains the chat which has carlos's password.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1185c1ec-0c85-40a3-b90e-79d8ed987219">


Pasword - jn2xhp4522lnktovm17a

Now login as carlos, to solve the lab.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ce318964-20cc-4770-826a-ed29e8971b29">



