## Lab Description:

<img width="889" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3fb77caf-8237-4860-bb02-123de615661e">


## Solutions:

Finding Users Table
The database in use here is Oracle, which holds the table information in the all_tables-table. I am interested in table_name. So I injected the query as payload UNION SELECT table_name, null from all_tables--.


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/036a798c-1d0c-4e0f-be8f-902fa24932ef">

Finding Column in User Table
The all_tab_columns-table holds information about the columns of each table, specifically the column_name column in Oracle Database. The proper string to inject is UNION SELECT column_name, null from all_tab_columns WHERE table_name = 'USERS_RQGNUR'--

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b53ee200-3535-4b20-a76a-71cd14585d2c">


Finding all Username and Password from that column
Now I have all details to obtain the required usernames and passwords. I inject UNION SELECT USERNAME_DEDQSJ,PASSWORD_NXDWXA from USERS_RQGNUR-- to form this query:

<img width="1438" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/319c3548-a24c-4ed0-b7c0-8424e80c53ae">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/163e6d74-53e8-411d-844c-0e796bd06497">


<img width="1226" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/834fcd22-336f-4082-89cc-4a92162834c2">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5bdd36fd-d3eb-46f1-af59-8fe4d575e14d">






The last step I logged in the website as administrator

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8b8dbf7e-05ee-4b53-92d0-c93d53b236f8">


