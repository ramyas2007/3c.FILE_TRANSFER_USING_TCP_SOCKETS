# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## SERVER
```
import socket

port = 8000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(1)
print("Server listening...")

conn, addr = s.accept()
print("Got connection from", addr)

data = conn.recv(1024)
print("Server received:", data.decode())

filename = r"C:\Users\admin\Documents\CN EXPS\mytext.txt"
with open(filename, 'rb') as f:
    while True:
        l = f.read(1024)
        if not l:
            break
        conn.send(l)

print("Done sending file")
conn.close()
```
## CLIENT
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 8000
s.connect((host, port))
s.send("Hello server!".encode())

received_path = r"C:\Users\admin\Documents\CN EXPS\received_file.txt"
with open(received_path, 'wb') as f:
    while True:
        data = s.recv(1024)
        if not data:
            break
        f.write(data)

print('Successfully received the file at', received_path)
s.close()
```

## OUPUT
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/e8bacd0a-5360-476e-9c03-e975afabb939" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/6b7b14dc-d3e2-4309-9185-26c93b15e126" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
