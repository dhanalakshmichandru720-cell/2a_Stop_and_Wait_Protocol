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
import time

client = socket.socket()
client.connect(('localhost', 8000))
client.settimeout(5)  

while True:
    msg = input("Enter a message (or type 'exit' to quit): ")

    client.send(msg.encode())  

    if msg.lower() == 'exit':  
        print("Connection closed by client")
        client.close()
        break

    try:
        ack = client.recv(1024).decode()
        if ack == "ACK":
            print(f"Server acknowledged: {ack}")
    except socket.timeout:
        print("No ACK received, retransmitting...")
        continue
```
## SERVER
```
import socket

server = socket.socket()
server.bind(('localhost', 8000))
server.listen(1)
print("Server is listening...")
conn, addr = server.accept()
print(f"Connected with {addr}")

while True:
    data = conn.recv(1024).decode()

    if data:
        print(f"Received: {data}")
        conn.send("ACK".encode())

        if data.lower() == 'exit':  
            print("Connection closed by client")
            conn.close()
            break
```
## OUTPUT
<img width="1100" height="157" alt="Screenshot 2026-03-12 111919" src="https://github.com/user-attachments/assets/ffc36a51-2cba-4d91-b501-548118079bae" />
<img width="1066" height="214" alt="Screenshot 2026-03-12 111927" src="https://github.com/user-attachments/assets/bbd77ef7-88f0-4df0-aa32-05a28598ba2e" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
