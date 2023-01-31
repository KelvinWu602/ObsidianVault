#networking 

There two main protocols:
1. TCP
	1. HTTP
	2. FTP
	3. SMTP
	4. Telnet
2. UDP
	1. [[Internet Protocol#DHCP|DHCP]]
	2. [[Internet Protocol#DNS (Get IP)|DNS]]
	3. SNMP
	4. TFTP
	5. VolP
	6. IPTV

# TCP

## Properties
- Reliable
- Error Detection: Acknowledge
- Error Correction: Retransmission
- Sequencing

## Sequencing

Data from Application Layer is often too big for the IP protocol packet. 

```mermaid
flowchart LR
	Data --> Segment1
	Data --> Segment2
	Data --> Segment3
	Data --> Segment4
```
Sending order $\ne$ Receiving order, therefore we have sequence numbers.

## Three-way Handshake

Using three-way handshake can ensure both sides are awaring of the message.

```mermaid
sequenceDiagram
	A ->> B : SYN x, SPort a, DPort b
	B ->> A : SYN y, ACK x+1, SPort b, DPort a
	A ->> B : ACK y+1, SPort a, DPort b
```
- Sequence numbers are randomly chosen.


## Acknowledge

When the receiver does not send ACK in time, data will be retransmitted.
To retransmit right segment, there is a retransmission queue.
The retransmission queue is cleared once an ACK is received.

Retransmission examples:
```mermaid
sequenceDiagram
	A ->> B : SYN 1
	A --x B : SYN 2
	A ->> B : SYN 3
	B ->> A : ACK 2, ws = 1
	A ->> B : SYN 2
	B ->> A : ACK 4, ws = 2
	A ->> B : SYN 4
	A ->> B : SYN 5
	B --x A : ACK 6
	A ->> B : SYN 4
	A ->> B : SYN 5
	B ->> A : ACK 6
```


## Multiplexing with Ports

Ports are used to identify which process does this message belongs to.
TCP Software is responsible for feeding the message data to correct process.

>[!Note] Demultiplex
> Delivering data from the transport layer to the correct port process.

### Well-Known Ports
- Numbers below 1024
- Defined by Internet Assigned Number Authority
![[Pasted image 20221203220347.png]]

### Registered Port
- 1024 to 49151
- For applications use

### Dynamic or Private Ports
- 49152 to 65535
- Dynamically assigned to applications


## Flow control with window size

Windows size = number of segments per ACK
Every process has a network io buffer. When the process is running slow, the buffer can be full. Then it needs to adjust the window size in time.

E.g. windows size = 3

```mermaid
sequenceDiagram
	A ->> B : SYN 1
	B ->> A : ACK 2
	A ->> B : SYN 2
	A ->> B : SYN 3
	A ->> B : SYN 4
	B ->> A : ACK 5
```



# UDP

## Properties
- Fast
- Unreliable

## Port
Same as TCP.