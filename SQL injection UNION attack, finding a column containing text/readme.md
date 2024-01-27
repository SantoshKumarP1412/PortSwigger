## Lab Description:

<img width="888" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/6fef9230-8211-40fe-9f90-7a08ec4e943f">


## Solution:

*Query*

```SELECT * FROM someTable WHERE category = '<CATEGORY>'```

We need to use the UNION SELECT payload using 3 NULL values. Try thetring value 33eWHU in one NULL value to see if it returns that string. If it does , then it means the column contains string data else it is not sting data.


![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/7d878d13-406c-4ea6-b95e-04a889500ce7)



![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d4ada523-cf05-48fb-b610-1ba4d1470b42)



![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2362d9c7-ac5a-4bcc-96e9-49fc356ea28c)
