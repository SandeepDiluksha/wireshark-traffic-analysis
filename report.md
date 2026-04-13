# Network Traffic Analysis Report
### Captured and analyzed using Wireshark on Ubuntu Linux

---

## Section 1 — TCP Three Way Handshake

### What is the TCP three way handshake?
The TCP three way handshake is the process by which a reliable connection
is established between two hosts before any data is exchanged. It consists
of three packets — SYN, SYN-ACK, and ACK.

### Capture details
- **Target:** example.com ()
- **Protocol:** HTTP (port 80)
- **Tool used:** curl http://example.com

### Packet analysis

**Packet 1 — SYN**
- Source: 192.168.215.229:59498
- Destination: 172.66.147.243:80
- Sequence number: 1853547140
- Flags: SYN=1, ACK=0
- Meaning: My laptop initiates a connection request to example.com

**Packet 2 — SYN-ACK**
- Source: 172.66.147.243:80
- Destination: 192.168.215.229:59498
- Sequence number: 3816164269
- Acknowledgment number: 1853547141
- Flags: SYN=1, ACK=1
- Meaning: Server acknowledges the request and sends its own sync signal

**Packet 3 — ACK**
- Source: 192.168.215.229:59498
- Destination: 172.66.147.243:80
- Acknowledgment number: 3816164270
- Flags: SYN=0, ACK=1
- Meaning: My laptop acknowledges the server's sync — connection established

### Why this matters
Without this handshake TCP cannot guarantee reliable delivery. The sequence
numbers established here are used for the rest of the connection to track
which packets have been received and which need to be retransmitted.

### Screenshot
![TCP Handshake](screenshots/tcp-conversation.png)
