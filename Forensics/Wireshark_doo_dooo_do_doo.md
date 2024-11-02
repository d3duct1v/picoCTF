# Wireshark doo dooo do doo...
Medium\
Forensics\
picoCTF 2021\
Author: Dylan
#### Description
Can you find the flag? [shark1.pcapng](https://mercury.picoctf.net/static/d6f9aa16d2a2c51d2e431e658d87af9e/shark1.pcapng).
## Solution
Well, we have a whole PCAP file full of HTTP traffic, bet we'll find the flag there.

Let's see if we can find this thing.  Using the `Statistics > HTTP > Requests` we can see we have 3 websites that are being visted.  The root and instance-action both have 1, and the windomain has 142.  Let's start with the easier ones. 

`http.request.method == GET`

This results in 2 packets, 1 from the root, and 1 from the instance-action.  Let's right click on the root packet and follow the TCP Stream.  At the bottom of the stream we have what looks to be our flag format, but it's off.  Let's copy that out and put it in CyberChef.

![Screenshot 2024-11-02 at 5 12 49 PM](https://github.com/user-attachments/assets/5952f128-a69c-47f1-a06a-25978a95becb)

Since we don't know exactly what it is in the format we expect to find, let's try the ROT13.  

CyberChef Recipe:\
`ROT13(true,true,false,13)`
### Flag
`The flag is picoCTF{p...f}`
