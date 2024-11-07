# PcapPoisoning
Medium\
Forensics\
picoCTF 2023\
pcap\
Author: Mubarak Mikail
#### Description
> How about some hide and seek heh?  Download this [file](https://artifacts.picoctf.net/c/375/trace.pcap) and find the flag.
## Solution
After downloading and opening the PCAP file in Wireshark, we have a lot of FTP data. The first five packets show a malformed IPv6 packet, a connection to port 22 (SSH), a ping, an FTP connection attempt, and a malformed DNS.

On the FTP packet, we want to follow the TCP Stream.  In the TCP Retransmission, we find our flag.

![Screenshot 2024-11-06 at 9 00 56 PM](https://github.com/user-attachments/assets/c201d4fb-06f1-46e3-9836-209721e918ee)

### Flag
`picoCTF{P...1}`
