# Big Zip
Easy
General Skills
picoGym Exclusive
Author: LT 'syreal' Jones
#### Description
> Unzip this archive and find the flag.  [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)
## Solution
Download and extract the zip file.  This zip file contains a lot of text files, and folders with more text files in them.  The easiest way to find the flag is using a bash for loop to grep each file for the flag.
```bash
for i in $(find . -name "*.txt"); do grep "picoCTF" $i; done
```

![Screenshot 2024-11-05 at 9 28 44 PM](https://github.com/user-attachments/assets/90aa2b3a-a93a-4da7-8915-af24f1c2e3bd)

### Flag
`picoCTF{g...c}`
