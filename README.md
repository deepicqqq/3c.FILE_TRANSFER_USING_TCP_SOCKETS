# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
NAME:DEEPIKA P\
REFERENCE NO:212223240024
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### CLIENT
```
import socket 
s = socket.socket() 
host = socket.gethostname() 
port = 60000 
s.connect((host, port)) 
s.send("Hello server!".encode()) 
with open('received_file', 'wb') as f: 
    while True: 
        print('receiving data...') 
        data = s.recv(1024) 
        print('data=%s', (data)) 
        if not data: 
            break 
        f.write(data) 
f.close() 
print('Successfully get the file') 
s.close() 
print('connection closed')
```

### SERVER
```
import socket                    
port = 60000                    
s = socket.socket()              
host = socket.gethostname()      
s.bind((host, port))
s.listen(5)                      
while True: 
    conn, addr = s.accept()      
    data = conn.recv(1024) 
    print('Server received', repr(data)) 
    filename='mytext.txt' 
    f = open(filename,'rb') 
    l = f.read(1024) 
    while (l): 
       conn.send(l) 
       print('Sent ',repr(l)) 
       l = f.read(1024) 
    f.close() 
    print('Done sending') 
    conn.send('Thank you for connecting'.encode()) 
    conn.close()
```
## OUPUT
### CLIENT
![310377744-396ffe7b-e40b-496d-9f4e-feb5b2fbc76b](https://github.com/nivetharajaa/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/120543388/96473afa-18d0-4295-a365-668d074756ad)

### SERVER
![310377797-e9b63c37-6b87-4b59-b277-fa5d3ba1ca0e](https://github.com/nivetharajaa/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/120543388/9295a11c-3e23-4cf1-a8bb-b0b11078dc30)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
