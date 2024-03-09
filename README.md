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
# client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
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
# server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())


```
## OUPUT
# client:
![Screenshot 2024-03-10 001742](https://github.com/Gokztechz/2b_SLIDING_WINDOW_PROTOCOL/assets/117667038/c9b6be79-fbce-4f43-a98b-f686ab8dd137)
# server:

![Screenshot 2024-03-10 001758](https://github.com/Gokztechz/2b_SLIDING_WINDOW_PROTOCOL/assets/117667038/bba32f0c-e817-4f74-b398-81f2f3f89817)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
