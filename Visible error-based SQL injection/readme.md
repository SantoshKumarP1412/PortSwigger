Lab Description:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0eeb7598-dd63-4f9d-9c78-9a6cd03c8360)

Solution:

Let's try to input a special character ' in the TrackingID parameter since it is vulnerable as per lab description to try and induce an SQL error.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8e53329c-cac5-49ca-aa02-b4b3fe22e85e)

Now we induced an error in the application and so we got an error response back which leaked the query being made in the backend.

Since we know what query is being made, now we can craft our payload using CAST conditional expresiions.

First we give a generic SELECT query & CAST the returned value to int datatype.

```TrackingId=7Ny9HYpA5twt8bPQ' AND CAST((SELECT 1) AS int)--```

The subquery (SELECT 1) is selecting the value 1 from the database. The CAST function is then used to convert that value into an integer data type (AS int).

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/7c0673d8-e1f2-4253-b545-387b80d7eb1b)

The query is being truncated here. So lets either remove some or all of trackingID cookie value to free up some space.
```TrackingId=' AND 1=CAST((SELECT username FROM users) AS int)--;```

<img width="1204" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/16757692-936f-489a-be9c-c903567b02dd">

Modify the query to return only 1 row,

```TrackingId=' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--```

<img width="1211" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/05f44005-c728-47dc-8cc8-51e777433da3">

It tries to retrieve the username column from the users table using the subquery (SELECT username FROM users LIMIT 1). The LIMIT 1 clause ensures that only one row(first row) is returned.

The obtained username is then cast as an integer using the CAST function.(WHY ? - To retrieve the obtained info via the error responses) EG - It may produce error like User shebu is not an integer


Now that we know that administrator is the first user in the users table , let's retreive his password.

```TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--```

Here in this payload we didn't giove WHERE username="administrator" because LIMIT 1 ensures that it retreives the info of first column which in this case is the administrator.

Thus we got the password of the admin user via error response.

<img width="1209" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5f57d9c1-4433-46f0-978a-69fd811127a8">

Admin Credentials - administrator:k179uhgv11hrqm7fcko9

Now login as admin in the shopping website to solve the lab.


<img width="1229" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9163f044-34d1-4152-8a2c-6577649be2ac">

