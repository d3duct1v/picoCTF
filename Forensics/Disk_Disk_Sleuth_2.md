# Disk, disk, sleuth! II
Medium\
Forensics\
picoCTF 2021\
Author: syreal
#### Description
All we know is the file with the flag is named `down-at-the-bottom.txt`... Disk image: dds2-alpine.flag.img.gz
## Solution
Download and unzip the gunzip file.  Using the `mmls` we can find the start point of the linux partition.

![Screenshot 2024-10-22 at 4 07 47 PM](https://github.com/user-attachments/assets/f760c1fc-ceab-4aa6-8806-00289fc7ce73)

Next we can start looking for the file.  `fls` has 2 options that allow us to display the full file and recursively list the directory entries.  Combining this with `grep` we should be able to locate the file fast. 

`fls -r -p -o 2048 dds2-alpine.flag.img | grep down-at-the-bottom.txt`\
![Screenshot 2024-10-22 at 4 08 23 PM](https://github.com/user-attachments/assets/5f41d477-fce7-4636-b18e-326741d2e83f)

Lets output that text file to the local system:

`icat -o 2048 dds2-alpine.flag.img 18291`\
![Screenshot 2024-10-22 at 4 09 21 PM](https://github.com/user-attachments/assets/ea747a86-da17-4997-82e5-f8d5827bb197)

`down-at-the-bottom.txt`\
![Screenshot 2024-10-22 at 4 10 28 PM](https://github.com/user-attachments/assets/19144711-c89c-4ff7-95e9-27d009349bb4)

### Flag
```
picoCTF{f...d}
```
