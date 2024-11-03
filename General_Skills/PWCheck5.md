# PW Crack 5
Medium\
General Skills\
Beginner pico\
Mini 2022\
password_cracking\
hashing\
Author: LT 'syreal' Jones
#### Description
> Can you crack the password to get the flag?  Download the password checker [here](https://artifacts.picoctf.net/c/33/level5.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/33/level5.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/33/level5.hash.bin) in the same directory too. Here's a [dictionary](https://artifacts.picoctf.net/c/33/dictionary.txt) with all possible passwords based on the password conventions we've seen so far.
## Solution
Like PW Crack 4, we have the same program structure but this time we have a dictionary list of 65536 possibilities.  Following the previous solution, we'll add a break feature.

```bash
for i in `cat dictionary.txt`; do echo $i | python3 level5.py | grep "picoCTF" && break; done
```

![Screenshot 2024-11-03 at 2 33 28 PM](https://github.com/user-attachments/assets/5121627b-7620-4ca7-8516-d2eb4af1f756)

### Flag
`picoCTF{h...3}`
