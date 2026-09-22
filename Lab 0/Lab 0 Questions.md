## 1) Website Accessed

The website that I accessed is the French Wikipedia (fr.wikipedia.org), which can be seen in the TLS Client Hello packet (packet 21980).

<img width="212" height="70" alt="image" src="https://github.com/user-attachments/assets/a8f8a69b-1048-4292-9829-9b6d31c8912c" />


## 1.1) Server Details

* **IP Address:** 103.102.166.224
  <img width="1430" height="243" alt="Screenshot 2026-09-22 at 13 51 46" src="https://github.com/user-attachments/assets/fc53953e-3758-492c-a444-499a275e2b2e" />

* **Port Number:** 443 (the standard port for secure HTTPS traffic)
<img width="1430" height="428" alt="Screenshot 2026-09-22 at 13 52 32" src="https://github.com/user-attachments/assets/e449d789-df6f-473b-9371-aa3426d0d5e7" />


## 1.2) PC Details

* **IP Address:** 10.119.82.29

* **Source Port Number:** 53631


## 1.3) The TCP Three-Way Handshake Process

The three-way handshake is how a computer and a server establish a reliable connection before sending actual website data. It happens in three steps:

1. **SYN (Synchronize):** The client (the PC) sends a packet to the server asking to start a connection.
2. **SYN-ACK (Synchronize-Acknowledge):** The server receives the request, agrees to start the connection, and sends a packet back to acknowledge the client's request.
3. **ACK (Acknowledge):** The client receives the server's agreement and sends one final packet back to confirm that the connection is set up.

## 1.4) Identifying the Packets in the Capture

* **SYN Packet:** Packet 21972 is the initial request from the PC to the server. 
 
* **SYN-ACK Packet:** Packet 21977 is the server's reply back to the PC, acknowledging the request.

* **ACK Packet:** Packet 21978 is the PC's final confirmation to the server, completing the handshake.


## 2) DNS Packet Analysis

<img width="1436" height="313" alt="image" src="https://github.com/user-attachments/assets/0f42c713-5b99-40a8-aed8-d7f78e3ac830" />

**2.1) What are the IP address and port number of the DNS server?**

* **IP address:** 140.118.31.99
  
* **Destination port:** 53
  

**2.2) What is the domain name in the DNS query?**

* youtube.com
  
**2.3) Which protocols does this DNS packet use? List the protocols from Layer 2 to Layer 5 in the TCP/IP five-layer model:**

* **Layer 2 (Link):** Ethernet II
  

* **Layer 3 (Network):** IPv4 (Internet Protocol Version 4)
  

* **Layer 4 (Transport):** UDP (User Datagram Protocol)
  

* **Layer 5 (Application):** DNS (Domain Name System)


## 3) HTTP Packet Analysis

<img width="1436" height="608" alt="image" src="https://github.com/user-attachments/assets/74c6082d-de27-4c09-8e0f-6c2db295b353" />

**3.1) Which HTTP page did you access?**

* http://www.gzxyzn.com/Article/bjrk2/1644.html (The host "www.gzxyzn.com" is visible in the packet bytes pane, and the path "/Article/bjrk2/1644.html" is in the Info column).
<img width="1436" height="732" alt="image" src="https://github.com/user-attachments/assets/1987d4ff-2458-400d-a551-6f82383890b9" />


**3.2) What are the IP address and port number of the server hosting the page?**

* **IP address:** 61.183.8.129


* **Port number:** 80

**3.3) What is the HTTP request method?**

* GET


**3.4) What is the HTTP response status code, and what does it mean?**

* **Status code:** 200 OK (Visible in packet 652943 right below your selected request).


* **Meaning:** The request was successful, and the server successfully delivered the requested webpage data to the client.





