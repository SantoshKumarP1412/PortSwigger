## Lab Description:

<img width="941" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/cbe75d70-2c85-4283-be46-d34590a2fcb3">

## Solution:

Login as admin -
First lets familiarize ourselves by logging in as admin.

Clicking on admin panel link after logging in, takes us to this page where we can change privileges of a user.

When we upgrade carlos user privileges, the request sent is as follows,

<img width="618" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/84d5fa26-90c0-4708-9e3d-ed5b3f38254d">

We can see that it has a referrer header which points to /admin.

<img width="1188" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/8ccbf42f-86c9-4399-8108-6ed96985fb44">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/ceb411ea-d58b-4612-9539-27f717005204">

