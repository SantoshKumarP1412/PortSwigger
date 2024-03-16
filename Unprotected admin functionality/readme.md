## Lab Description:

<img width="897" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a24b1e23-83ea-4295-aca3-e73f0d7321fb">

## Solution:

When the lab loads, we get the ususal shopping website.

Clicking on My Account page takes us to /login endpoint

<img width="1364" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/110b0afd-58df-493b-a5d1-105864042d27">

Now we need to bypass this login page and directly access the admin page.

For that we can look for one of the common web directories like the robots.txt and sitemap.xml

```robots.txt```

<img width="1047" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/15fdd49c-6f40-4fc1-ac9f-6a9fab43801b">

We see a disallowed login entry here for the admin panel which is /administrator-panel.

On visiting the /administrator-panel directory, we get the admin panel.

<img width="978" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d50a9361-3c3d-41f2-b102-42e8c8d2fe88">

So we click the link to delete the user carlos to solve the lab.


<img width="1411" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/fdb79e92-66bb-47e8-baee-b547937e6fb1">
