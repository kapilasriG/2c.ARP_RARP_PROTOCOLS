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
import socket

# Create socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server is listening on port 8000...")

# Accept connection
c, addr = s.accept()
print("Connection established with:", addr)

# Dictionary of IP to MAC
address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

# Infinite loop to handle client requests
while True:
    ip = c.recv(1024).decode()   # Receive IP from client
    if not ip:                   # If client disconnects
        break
    try:
        c.send(address[ip].encode())   # Send MAC if found
    except KeyError:
        c.send("Not Found".encode())   # Send error if not found

# Close connection
c.close()
```
## OUPUT - ARP
<img width="1920" height="1080" alt="Screenshot 2026-05-13 103027" src="https://github.com/user-attachments/assets/15c1445b-2dda-46e9-9d0c-7d1b5ec31a4e" />

## PROGRAM - RARP
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1920" height="1080" alt="Screenshot 2026-05-13 103109" src="https://github.com/user-attachments/assets/aff3ecee-f62f-4db1-a6d1-fb41a0695118" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
