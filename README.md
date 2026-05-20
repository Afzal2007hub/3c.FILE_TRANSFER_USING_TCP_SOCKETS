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
#### fileserver.py
~~~
import socket

server = socket.socket()

server.bind(("127.0.0.1", 5555))
server.listen(1)

print("Server waiting for connection...")

client, addr = server.accept()
print("Connected to:", addr)

filename = input("Enter file name to send: ")

with open(filename, "rb") as file:
    data = file.read()
    client.send(data)

print("File sent successfully")

client.close()
server.close()
~~~
#### fileclient.py
~~~
import socket

client = socket.socket()

client.connect(("127.0.0.1", 5555))

save_name = input("Enter name to save file: ")

data = client.recv(1000000)

with open(save_name, "wb") as file:
    file.write(data)

print("File received successfully")

client.close()
~~~
## OUPUT
#### fileserver.py
<img width="599" height="109" alt="image" src="https://github.com/user-attachments/assets/21837f65-7095-4fbe-92f8-af835a2e0f0a" />
#### fileclient.py
<img width="579" height="64" alt="image" src="https://github.com/user-attachments/assets/c0f62876-7eec-4097-8b5a-4fe69ae2f8f0" />
#### sample.txt
<img width="739" height="199" alt="image" src="https://github.com/user-attachments/assets/9a39b312-8ed0-4b68-8871-9482a179a74a" />

#### received.txt
<img width="615" height="150" alt="image" src="https://github.com/user-attachments/assets/2e32a747-bb06-465e-94fa-137738b316d7" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
