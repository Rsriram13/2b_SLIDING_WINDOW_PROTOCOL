# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To implementation of sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send: "))
l=list(range(size))
s=int(input("Enter Window Size: "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
### SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recieved from the server".encode())
```

## OUPUT
### CLIENT
![output](https://github.com/Rsriram13/2b_SLIDING_WINDOW_PROTOCOL/assets/145742823/9b236133-33f1-4321-8b92-edafea8171ad)
### SERVER
![output](https://github.com/Rsriram13/2b_SLIDING_WINDOW_PROTOCOL/assets/145742823/ed0db7ea-c66d-4d86-bc65-ed1642ef2492)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
