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
## PROGRAM - ARP
CLIENT:
```python
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
SERVER:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
     ip=input("Enter logical Address : ") 
     s.send(ip.encode()) 
     print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
CLIENT :

<img width="520" height="201" alt="Screenshot 2025-10-08 191257" src="https://github.com/user-attachments/assets/79133fb0-ae39-4163-9e46-34782b010ca7" />


SERVER:

<img width="512" height="192" alt="image" src="https://github.com/user-attachments/assets/9de3005c-2a92-49fa-9842-f249193cf638" />

## PROGRAM - RARP
CLIENT:
```python
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
SERVER:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
CLIENT:


<img width="521" height="190" alt="Screenshot 2025-10-08 193547" src="https://github.com/user-attachments/assets/a6bbe148-d7df-4e21-9e49-53db36065c3b" />


SERVER:

<img width="497" height="190" alt="image" src="https://github.com/user-attachments/assets/b43e73a7-899f-4d87-870a-665b4abab065" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
