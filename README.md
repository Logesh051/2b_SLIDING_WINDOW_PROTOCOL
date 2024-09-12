# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write python program to perform sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size :"))
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

## Server

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from server".encode())
```
## OUPUT
![366394875-513c3bd3-95af-464c-9a41-38a3ae9e701c](https://github.com/user-attachments/assets/3f892753-d6ed-495d-9a75-b706ff689893)
![366394932-560a4eba-1927-4395-afe7-550ca7d61c93](https://github.com/user-attachments/assets/2ed0bc8e-597a-4fc7-b7a5-0e27ec234847)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
