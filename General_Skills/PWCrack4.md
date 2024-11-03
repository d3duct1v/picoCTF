# PW Crack 4
Medium\
General Skills\
Beginner pico\
Mini 2022\
password_cracking\
hashing\
Author: LT 'syreal' Jones
#### Description
> Can you crack the password to get the flag?  Download the password checker [here](https://artifacts.picoctf.net/c/20/level4.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/20/level4.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/20/level4.hash.bin) in the same directory too.  There are 100 potential passwords with only 1 being correct. You can find these by examining the password checker script.
## Solution
We can see three functions after downloading the files and loading the Python file into Visual Studio Code.

Similar to PW Crack 3, we have the same program structure to include the possible password list.
```python
...
# The strings below are 100 possibilities for the correct password.
# (Only 1 is correct)
pos_pw_list = ["158f", "1655", "d21e", "4966", "ed69", "1010", "dded", "844c", "40ab", "a948", "156c", "ab7f", "4a5f", "e38c", "ba12", "f7fd", "d780", "4f4d", "5ba1", "96c5", "55b9", "8a67", "d32b", "aa7a", "514b", "e4e1", "1230", "cd19", "d6dd", "b01f", "fd2f", "7587", "86c2", "d7b8", "55a2", "b77c", "7ffe", "4420", "e0ee", "d8fb", "d748", "b0fe", "2a37", "a638", "52db", "51b7", "5526", "40ed", "5356", "6ad4", "2ddd", "177d", "84ae", "cf88", "97a3", "17ad", "7124", "eff2", "e373", "c974", "7689", "b8b2", "e899", "d042", "47d9", "cca9", "ab2a", "de77", "4654", "9ecb", "ab6e", "bb8e", "b76b", "d661", "63f8", "7095", "567e", "b837", "2b80", "ad4f", "c514", "ffa4", "fc37", "7254", "b48b", "d38b", "a02b", "ec6c", "eacc", "8b70", "b03e", "1b36", "81ff", "77e4", "dbe6", "59d9", "fd6a", "5653", "8b95", "d0e5"]
...
```

Again, create a new file with the passwords.  Use a for loop, and, this time, grep for the flag.
```bash
for i in `cat pw_list.txt`; do echo $i | python3 level4.py | grep "picoCTF"; done
```

![Screenshot 2024-11-03 at 2 14 12 PM](https://github.com/user-attachments/assets/49805406-cdd7-430e-8bb8-489e4ba966e3)

### Flag
`picoCTF{f...}`
