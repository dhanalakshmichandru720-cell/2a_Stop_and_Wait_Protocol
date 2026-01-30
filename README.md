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
## CLIENT
```
import socket

# create socket
s = socket.socket()

# connect to server
s.connect(('localhost', 8000))

while True:
    msg = input("Enter data: ")
    s.send(msg.encode())
    ack = s.recv(1024).decode()
    print("Server:", ack)
```
## SERVER
```
import socket

# create socket
s = socket.socket()

# bind IP and port
s.bind(('localhost', 8000))

# listen for client
s.listen(1)
print("Server waiting for connection...")

# accept client
c, addr = s.accept()
print("Connected from", addr)

while True:
    data = c.recv(1024).decode()
    if not data:
        break
    print("Client:", data)
    c.send("ACK received".encode())

c.close()
```
## OUTPUT
<img width="936" height="248" alt="Screenshot 2026-01-30 175036" src="https://github.com/user-attachments/assets/99125cc4-74a0-48bd-a553-5a8300a97602" />
<img width="1123" height="193" alt="Screenshot 2026-01-30 175024" src="https://github.com/user-attachments/assets/bba5a931-0d7e-4921-8a72-be3dae988adc" />
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
