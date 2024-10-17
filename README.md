# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
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
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter window size : "))
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
## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
## OUPUT
## CLIENT
![ex2b c](https://github.com/user-attachments/assets/d2f5b3d3-762c-4466-8db9-9dbf45123881)

## SERVER
![ex2b s](https://github.com/user-attachments/assets/182b7529-1fd2-47fe-833f-a808d0abf9ed)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
