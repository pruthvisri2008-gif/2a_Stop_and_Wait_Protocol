# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
~~~
server.py

import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server is waiting for connection...")
c, addr = s.accept()
print("Connected to:", addr)
while True:
    data = c.recv(1024).decode()
    if not data:
        break
    print("Client:", data)
    c.send("Acknowledgement Received".encode())
c.close()

client.py

import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    msg = input("Enter data: ")
    s.send(msg.encode())
    ack = s.recv(1024).decode()
    if ack:
        print("Server:", ack)
    else:
        break
s.close()
~~~

## OUTPUT
<img width="1472" height="344" alt="cn exp02a" src="https://github.com/user-attachments/assets/697366e5-dbba-40bc-88f6-bb41d91d0535" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
