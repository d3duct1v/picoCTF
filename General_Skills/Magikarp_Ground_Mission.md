# Magikarp Ground Mission
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
> Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `abcba9f7`

> Additional details will be available after launching your challenge instance. `ssh ctf-player@venus.picoctf.net -p 49960`
## Solution
Start the CTF instance, and then copy the ssh command and connect to the server.

Once connected, listing the directory, you will find `1of3.flag.txt`.  Now we know what to look for, using the `find` command `find / -name "*flag.txt"`.  Now, read each file to get all the parts of the flag.
```bash
ssh ctf-player@venus.picoctf.net -p 49960
# Home directory
cat 1of3.flag.txt
cat /2of3.flag.txt
cd ~
cat 3of3.flag.txt
```
### Flag
`picoCTF{x...3}`
