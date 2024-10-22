# information
##### Tags
Easy\
Forensics\
picoCTF 2021\
Author: susie
#### Description
> Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/7cf6a33f90deeeac5c73407a1bdc99b6/cat.jpg)
## Solution
Download the file and use `exiftool` to view the metadata. 

![Screenshot 2024-10-22 at 3 04 03 PM](https://github.com/user-attachments/assets/1418d9c5-c6d6-476d-a4de-64a4111cef0d)

Either use the command line or CyberChef to undo the base64
`echo "<base64>" | base64 -d`

![Screenshot 2024-10-22 at 3 04 29 PM](https://github.com/user-attachments/assets/c32ab990-a004-41a1-9dd3-5827f1a95ce7)

CyberChef Recipe:
```
From_Base64('A-Za-z0-9+/=',true,false)
```

### Flag
`picoCTF{t...d}`
