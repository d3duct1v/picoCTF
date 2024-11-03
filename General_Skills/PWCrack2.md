# PW Crack 2
Easy\
General Skills\
Beginner pico\
Mini 2022\
password_cracking\
Author: LT 'syreal' Jones
#### Description
> Can you crack the password to get the flag?  Download the password checker [here](https://artifacts.picoctf.net/c/14/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/14/level2.flag.txt.enc) in the same directory too.
## Solution
We can see two functions after downloading the files and loading the Python file into Visual Studio Code.

Like PW Crack 1, the first function `str_xor` appears to be a decrypt function.  The next part reads in the encrypted file, and the following function is the program's start.  There is a comparison operator checking `user_pw` and a value.  In the previous line, `user_pw` is assigned by the user's input.  
```python
...
def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
...
```
We can figure out the password needed a few ways, manually with using a hex to ascii map [here](https://www.freecodecamp.org/news/ascii-table-hex-to-ascii-value-character-code-chart-2/), or with the command line or Python.

#### Bash
`echo -n 64653736 | xxd -r -p`\
Command Breakdown\
1. **`echo -n 64653736`**:
    - `echo` prints the specified text to standard output.
    - The `-n` option tells `echo` not to add a newline at the end, so it simply outputs the string `64653736`.
    - Here, `64653736` is a hexadecimal representation of some data.
2. **`| xxd -r -p`**:
    - The output of `echo -n 64653736` is piped (`|`) into `xxd`, which is a command-line tool for creating hex dumps and converting hex to binary.
    - `xxd -r` (reverse mode) converts the hex dump back to its original binary form.
    - `-p` (plain mode) tells `xxd` to interpret the input as plain hex digits without any additional formatting.
#### Python
```bash
python3 -c 'print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))'
```

Execute the Python script and enter the password.

![Screenshot 2024-11-03 at 12 49 40 PM](https://github.com/user-attachments/assets/b7c5d49f-98b3-4ee1-a3e7-1f7558129795)

### Flag
`picoCTF{t...a}`
