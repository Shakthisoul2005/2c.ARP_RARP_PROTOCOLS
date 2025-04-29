# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM 
```
CLIENT-ARP
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())

CLIENT-RARP
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
       ip=c.recv(1024).decode() 
       try: 
          c.send(address[ip].encode()) 
       except KeyError: 
          c.send("Not Found".encode())
```
```
 SERVER-ARP
 import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode()

SERVER-RARP
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
 ip=input("Enter MAC Address : ") 
 s.send(ip.encode()) 
 print("Logical Address",s.recv(1024).decode())
 ```
## OUPUT - ARP
CLIENT-ARP
![Screenshot 2025-04-15 131551](https://github.com/user-attachments/assets/8af9faa2-77bf-41a8-a0dc-5535dee11cb4)

CLIENT-RARP
![CN EX1](https://github.com/user-attachments/assets/08b12a90-9d7f-4fd0-89db-7246713be559)


SERVER-ARP
![cn 2c](https://github.com/user-attachments/assets/54e189ba-0056-4406-9f20-0df7bbfd7cd4)

SERVER-RARP
![CN EX](https://github.com/user-attachments/assets/4faa66db-392f-43a8-acdb-f40dd4b4a6f0)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
