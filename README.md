# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## PROGRAM
```
Server.py
import socket
from pythonping import ping
s = socket.socket()
# Bind to localhost and port
s.bind(('localhost', 8000))
# Listen for connections
s.listen(5)
print("Ping Server started... Waiting for connection")
# Accept connection
c, addr = s.accept()
print("Connected to:", addr)
while True:
    hostname = c.recv(1024).decode()
    if not hostname:
        break
    try:
        result = ping(hostname, count=4, verbose=False)
        c.send(str(result).encode())
    except:
        c.send("Host Not Found".encode())
c.close()

Client.py
import socket
# Create socket
s = socket.socket()
# Connect to server
s.connect(('localhost', 8000))
while True:
    website = input("Enter the website you want to ping: ")
    if website.lower() == "exit":
        break
    s.send(website.encode())
    result = s.recv(1024).decode()
    print("\nPing Result:\n", result)
s.close()

Traceroute.py
import os
print("Running Traceroute...\n")
os.system("C:\\Windows\\System32\\tracert.exe google.com")
```
```
## Output
<img width="924" height="373" alt="Screenshot 2026-05-25 224818" src="https://github.com/user-attachments/assets/86fe7222-178e-42c1-993a-7d0b6bb432e2" />
<img width="936" height="504" alt="Screenshot 2026-05-25 224844" src="https://github.com/user-attachments/assets/454035f0-d873-4968-8288-346d0d244902" />
<img width="945" height="678" alt="Screenshot 2026-05-25 224859" src="https://github.com/user-attachments/assets/1924a0f2-d9cf-4002-ba7b-7461c6b1f74e" />

## Result
Thus Execution of Network commands Performed 
