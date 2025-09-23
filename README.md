# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program to perform sliding window protocol 
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
   
## PROGRAM

**Client.py**

`````
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

size = int(input("Enter number of frames to send : "))
l = list(range(size))
s = int(input("Enter Window Size : "))
st = 0
i = 0

while True:
    while (i < len(l)):
        st = st + s
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print(ack)
            i += s
`````
**Server.py**

``````
import socket
s = socket.socket()
s.connect(('localhost', 8000))

while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```````

## OUTPUT

**Client.py**

<img width="479" height="210" alt="image" src="https://github.com/user-attachments/assets/287414a4-2028-40d3-bfc9-6aa41d41bce9" />

**Server.py**

<img width="520" height="157" alt="image" src="https://github.com/user-attachments/assets/c20bf04a-8508-44f3-9b9f-e3ce147f131e" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
