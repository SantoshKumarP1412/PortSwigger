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

T`He query is being truncated here. So lets either remove some or all of trackingID cookie value to free up some space.
```TrackingId=' AND 1=CAST((SELECT username FROM users) AS int)--;```
