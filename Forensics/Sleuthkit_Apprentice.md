# Sleuthkit Apprentice
##### Tags
Medium\
Forensics\
PicoCTF 2022\
disk\
Author: LT 'syreal' Jones
#### Description
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory. [Download compressed disk image](https://artifacts.picoctf.net/c/138/disk.flag.img.gz)
## Solution
Download and unzip the gunzip file.  Using the `mmls` we can find the start point of the linux partition.

![Screenshot 2024-10-25 at 4 39 22 PM](https://github.com/user-attachments/assets/efd0b6c2-72a0-4f2f-8a27-7d2578079dba)

Start searching with the root folder, then subfolder (my_folder), we can find the `flag.uni.txt` file.  We can then use `icat` to get the flag

![Screenshot 2024-10-25 at 4 39 34 PM](https://github.com/user-attachments/assets/f4b57993-b7de-4043-9ea6-f91c7fa47f61)

### Command List
```bash
mmls disk.flag.img
fls -o 360448 disk.flag.img
fls -o 360448 disk.flag.img 1995
fls -o 360448 disk.flag.img 3981
icat -o 360448 disk.flag.img 2371
```
### Flag
`picoCTF{b...4}`
