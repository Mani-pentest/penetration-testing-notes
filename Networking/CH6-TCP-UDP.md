# CH-6: TCP vs UDP

## TCP (Transmission Control Protocol)
**Definition** — A reliable, connection-oriented protocol 
that guarantees delivery of data. Establishes a connection 
before sending data.
- Used when accuracy matters more than speed
- Example: Like sending a registered post letter

## UDP (User Datagram Protocol)
**Definition** — A fast, connectionless protocol that sends 
data without confirming delivery.
- Used when speed matters more than accuracy
- Example: Video streaming, DNS, online gaming

## 3-Way Handshake
The process TCP uses to establish a connection:

Client          Server
|               |
|–– SYN —→  |  “Hello, can we talk?”
|               |
|←- SYN-ACK ––|  “Yes, I hear you!”
|               |
|–– ACK —→  |  “Great, let’s talk!”
|               |
|=== DATA ======|
