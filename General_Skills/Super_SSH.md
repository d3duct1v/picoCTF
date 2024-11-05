# Super SSH
Easy\
General Skills\
picoCTF 2024\
shell\
ssh\
browser_webshell_solvable\
Author: Jeffery John
#### Description
> Using a Secure Shell (SSH) is going to be pretty important. Additional details will be available after launching your challenge instance.

> Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `55457` to get the flag?  You'll also need the password `1ad5be0d`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)

## Solution
Use `SSH` to connect to the server, then copy the flag 
```bash
ssh ctf-player@titan.picoctf.net -p 55457
```
### Flag
`picoCTF{s...d}`
