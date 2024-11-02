# Packets Primer
Medium\
Forensics\
picoCTF 2022\
pcap\
Author: LT 'syreal' Jones
#### Description
Download the packet capture file and use packet analysis software to find the flag. [Download packet capture](https://artifacts.picoctf.net/c/194/network-dump.flag.pcap)
## Solution
Download the file and we find it's a PCAP file.  The packet capture is only 9 packets 4 ARPs (we can most likely ignore) 3 TCP and 1 S101 (whatever that is).

Let's start with the oddball: Packet 4. Once we select the packet, we see the flag was sent in its Data field.  

![Screenshot 2024-11-02 at 4 48 23 PM](https://github.com/user-attachments/assets/d9f93317-8fdd-4610-ad63-4fd71fda36e6)

Copy the Data.Value\
`7020692063206f204320542046207b207020342063206b20332037205f2035206820342072206b205f20632065...d0a`

Using CyberChef Recipe:
```
From_Hex('Auto')
Remove_whitespace(true,true,true,true,true,false)
```

### Flag
`picoCTF{p...}`
