# Trivial Flag Transfer Protocol
Medium\
Forensics\
picoCTF 2021\
Author: Danny
#### Description
Figure out how they moved the [flag](https://mercury.picoctf.net/static/88553d672efbccbc5868002f4c6eb737/tftp.pcapng).
## Solution
We have a lot of TFTP traffic let's see what Wireshark can export from the data.

Well we have 3 BMP pictures, an Instructions.txt, and plan files.  Let's save everything out.

Both instructions and plan are ROT13 encoded CyberChef: `ROT13(true,true,false,13)`.

**Instructions.txt**
```
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
```
Output
```
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN
```
**plan**
```
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF
```
Output
```
I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE. CHECK OUT THE PHOTOS
```

For each BMP file we can run steghide on them supplying the possible password in from the `plan` file contents.
```bash
for i in $(ls *.bmp); do steghide extract -p DUEDILIGENCE -sf $i; done
```

Looks like the last picture had our flag: _picture3.bmp_

![Screenshot 2024-11-02 at 5 29 58 PM](https://github.com/user-attachments/assets/26cea39b-0592-40d2-af04-bf2aa73dfcdb)

`cat flag.txt`

### Flag
`picoCTF{h...}`
