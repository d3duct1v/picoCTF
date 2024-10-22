# Disk, disk, sleuth!
##### Tags
Medium\
Forensics\
picoCTF 2021\
Author: syreal
#### Description
> Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: dds1-alpine.flag.img.gz
## Solution
Download and unzip the gunzip file.  Use the `srch_strings` and pipe (`|`) the output to `grep` and search term _pico_.

![Screenshot 2024-10-22 at 3 40 32 PM](https://github.com/user-attachments/assets/896f5cb4-0ec8-40c2-86ab-e93acde01192)

### Flag
`picoCTF{f...}`
