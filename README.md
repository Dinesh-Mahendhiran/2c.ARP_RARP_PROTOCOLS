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
## PROGRAM - ARP
```
SERVER PROGRAM ARP
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
```
```
CLIENT PROGRAM ARP
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
SERVER
<img width="1327" height="145" alt="image" src="https://github.com/user-attachments/assets/9d5f7cdd-5ba6-4e85-bed1-7ceb3c7824f3" />
CLIENT
<img width="1078" height="218" alt="image" src="https://github.com/user-attachments/assets/8e8fe478-db5c-44d3-b551-3ca790804a29" />

## PROGRAM - RARP
```
SERVER PROGRAM RARP
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
CLIENT PROGRAM RARP
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
SERVER 
<img width="1081" height="145" alt="image" src="https://github.com/user-attachments/assets/9e6f760c-35f7-469f-b1ff-b243bcdd6afd" />
CLIENT
<img width="1397" height="220" alt="image" src="https://github.com/user-attachments/assets/8045164b-3934-400f-9a01-99ccc8c4dbe2" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
