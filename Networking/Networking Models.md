#networking 
The Internet is an extremely complicated, distributed system. To understand it, one has to divide it into several layers. Networking model is the way to divide the Internet into different layers.

![[Pasted image 20221203121420.png]]

## OSI Model (7 layers)

1. Physical: bits
2. [[Ethernet|Data link]]: frames
3. [[Internet Protocol|Network]]: packets
4. [[Transport]]: segments
5. Session: data
6. Presentation: data
7. Application: data

## TCP/IP Model (4 layers)

1. Network Access: Controls the hardwares
		1. [[Ethernet]]
2. Internet: Path determination
		1. IP Protocol
			1. NAT
			2. ARP
		2. ICMP
3. Routing Protocols
		1. RIP
		2. EIGRP
4. Transport: Medium and device independent
		1. UDP
		2. TCP
5. Application: Represents data to the user
		1. DNS
		2. DHCP
		3. SMTP
		4. FTP
		5. HTTP

