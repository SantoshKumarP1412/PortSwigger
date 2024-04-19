##  SameSite Strict bypass via client-side redirect

<img width="908" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/78b50058-a012-4cd4-966e-79dca27f40e4">


## Solutions:

The POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass any SameSite cookie restrictions.

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/4f19b4de-a248-4aa0-acf9-937676f53019">

Identify the suitable vulnerable part

In the browser, go to one of the blog posts and post an arbitrary comment. Observe that you're initially sent to a confirmation page at /post/comment/confirmation?postId=x but, after a few seconds, you're taken back to the blog post.
<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/a39949cf-e633-4723-9ddc-ff28f64c9aba">


<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/5aad16d2-7841-493e-98a5-44b44f28e730">


Observe that the browser normalizes this URL and successfully takes you to your account page.

Bypass the SameSite restrictions

In the browser, go to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested. The following is one possible approach:

<script>
    document.location = "https://0a040032041a40b885a86270005e0019.web-security-academy.net/post/comment/confirmation?postId=/../../my-account";
</script>
Store and view the exploit yourself.

![Uploading image.png…]()
