# 2a_Stop_and_Wait_Protocol
-Ajmal Ali S 212224100003
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

CLINET:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server is listening...")

c, addr = s.accept()
print("Connection established with", addr)

while True:
    i = input("Enter data to send: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()
    if ack:
        print("Client:", ack)
        continue
    else:
        print("No acknowledgment received. Closing connection.")
        c.close()
        break
```
SERVER:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if data:
        print("Server:", data)
        s.send("Acknowledgement Received".encode())
    else:
        print("Connection closed by server.")
        s.close()
        break
```

## OUTPUT

CLIENT:

<img width="1305" height="339" alt="image" src="https://github.com/user-attachments/assets/355ec59f-3715-4343-bfb6-e0b43789762a" />

SERVER:

<img width="1478" height="283" alt="image" src="https://github.com/user-attachments/assets/127b85f1-2dfa-403b-8b8f-b13557ba9e45" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
