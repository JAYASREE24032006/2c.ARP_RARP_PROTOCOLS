# EX.NO.2c - SIMULATING ARP /RARP PROTOCOLS

**DATE : 13.03.2024**

## AIM:
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

**CLIENT**
```
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
**SERVER**
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
**CLIENT**
![image](https://github.com/JAYASREE24032006/2c.ARP_RARP_PROTOCOLS/assets/144360800/afec1b36-e9a3-47b6-bf4a-45972bd2f3bf)
**SERVER**
![image](https://github.com/JAYASREE24032006/2c.ARP_RARP_PROTOCOLS/assets/144360800/48a511e4-547d-46c4-b851-c11e4a72f722)


## PROGRAM - RARP
**CLIENT**
```
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
**SERVER**
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
**CLIENT**
![image](https://github.com/JAYASREE24032006/2c.ARP_RARP_PROTOCOLS/assets/144360800/7e7a6327-54fd-4781-826a-182a9a92b435)

**SERVER**

![image](https://github.com/JAYASREE24032006/2c.ARP_RARP_PROTOCOLS/assets/144360800/6f53bdc3-3c0b-429f-9fff-2331926ff051)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
