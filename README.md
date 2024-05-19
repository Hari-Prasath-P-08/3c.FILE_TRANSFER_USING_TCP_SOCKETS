# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

### Name: HARI PRASATH. P
### Reg. No: 212223230070

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:

### CLIENT:

```python
import socket

s = socket.socket()

host = socket.gethostname()

port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file', 'wb') as f:

    print('receiving data...')
    
    while True:
    
        data = s.recv(1024)
        
        print('data=%s', (data))
        
        if not data:
        
            break
        
        f.write(data)

print('Successfully received the file')

s.close()

print('connection closed')
```

### SERVER:

```python
import socket

port = 60000

s = socket.socket()

host = socket.gethostname()

s.bind((host, port))

s.listen(5)

print("Server listening on port", port)

while True:

    conn, addr = s.accept()
    
    print("Connected to", addr)
    
    data = conn.recv(1024)
    
    print('Server received', repr(data))
    
    filename = 'C:\\Users\\prabh\\OneDrive\\Desktop\\CODE\\CN\\SAMPLE.txt'
    
    with open(filename, 'rb') as f:
    
        l = f.read(1024)
        
        while l:
        
            conn.send(l)
            
            print('Sent', repr(l))
            
            l = f.read(1024)
    
    print('Done sending')
    
    conn.send('Thank you for connecting'.encode())
    
    conn.close()
```

## OUTPUT:

![326372191-33c3ee52-f171-4f21-9952-72ed107e3781](https://github.com/Hari-Prasath-P-08/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/139455593/749382ee-54d4-4d98-a99d-1322fc9fd4ed)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
