# strings it
Easy\
General Skills\
picoCTF 2019\
Author: Sanjay C/Danny Tunitis
#### Description
> Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings) without running it?
## Solution
Download the file and use strings and grep to find the flag.
```bash
strings strings | grep "picoCTF"
```
### Flag
`picoCTF{5...1}`
