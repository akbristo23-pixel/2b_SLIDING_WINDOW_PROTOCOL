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
client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost',8001)) 
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

server.py 

```
import socket 
s=socket.socket() 
s.connect(('localhost',8001)) 
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

## OUPUT
client.py

<img width="1325" height="321" alt="Screenshot 2026-11-14 090841" src="https://github.com/user-attachments/assets/279c90a3-f56f-4ba6-85ed-c176484bbf31" />

server.py

<img width="1320" height="278" alt="Screenshot 2026-11-14 090849" src="https://github.com/user-attachments/assets/5c1a054c-7d4e-437b-a1c3-e3612c5e71ce" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
