# PW Crack 3
Medium\
General Skills\
Beginner pico\
Mini 2022\
password_cracking\
hashing\
Author: LT 'syreal' Jones
#### Description
> Can you crack the password to get the flag?  Download the password checker [here](https://artifacts.picoctf.net/c/18/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/18/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/18/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
## Solution
We can see three functions after downloading the files and loading the Python file into Visual Studio Code.

Like PW Crack 1 & 2, the first function `str_xor` appears to be a decrypt function.  The next part reads in the encrypted file and hash in the binary file, and the following function creates a hash of the user-supplied password, and then the program starts.  

A comparison operator checks the `user_pw_hash` and the `correct_pw_hash`. In the previous line, the `user_pw` is assigned by the user's input.  

At the bottom of the script is a list of possible correct passwords. 
```python
...
pos_pw_list = ["8799", "d3ab", "1ea2", "acaf", "2295", "a9de", "6f3d"]
...
```
Moving forward, we can do this in two ways: modify the Python script or use the command line; in either case, a for loop will be used.

#### Bash
Copy the list to a new file (pw_list.txt) and place each password on its line.
```
8799
d3ab
1ea2
acaf
2295
a9de
6f3d
```
Now use a `for` loop to check each password.
```bash
for i in $(cat pw_list.txt); do echo $i | python3 level3.py; done
```

![Screenshot 2024-11-03 at 1 54 16 PM](https://github.com/user-attachments/assets/126e8f11-4e1b-4e65-bf4d-a6e7ee548098)

### Flag
`picoCTF{m...f}`
