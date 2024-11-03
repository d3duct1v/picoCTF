# PW Crack 1
Easy\
General Skills\
Beginner pico\
Mini 2022\
password_cracking\
Author: LT 'syreal' Jones
#### Description
> Can you crack the password to get the flag?  Download the password checker [here](https://artifacts.picoctf.net/c/12/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/12/level1.flag.txt.enc) in the same directory too.
## Solution
After downloading the files and loading the Python file into Visual Studio Code, we can see two functions.

The first function `str_xor` appears to be a decrypt function.  The next part reads in the encrypted file, and the following function is the program's start.  There is a comparison operator checking `user_pw` and a value.  In the previous line, `user_pw` is assigned by the user's input.  

So, running the program in the terminal prompts us for a password.  Let's pass the value from the comparison. 
```python
...
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "1e1a"):
        print("Welcome back... your flag, user:")
...
```

![Screenshot 2024-11-03 at 12 11 00 PM](https://github.com/user-attachments/assets/23d2628c-d2e0-4939-bc05-d36f9e4860b8)

### Flag
`picoCTF{5...}`
