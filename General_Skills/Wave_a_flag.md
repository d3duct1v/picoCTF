# Wave a flag
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
> Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/a00f554b16385d9970dae424f66ee1ab/warm) has extraordinarily helpful information...
## Solution
There are two ways to solve this.
### First
Make the ELF binary executable by changing the permissions.  Then call the program with the help flag `./warm -h`.
```bash
chmod +x warm
./warm -h
```

![Screenshot 2024-11-05 at 9 08 21 PM](https://github.com/user-attachments/assets/874d6860-cab4-46af-847a-83c987d911c6)

### Second
The second option is to use `strings` and `grep`.
```bash
strings warm | grep "picoCTF"
```

![Screenshot 2024-11-05 at 9 09 07 PM](https://github.com/user-attachments/assets/709291af-e418-4a0e-a542-a3fe9955b41f)

### Flag
`picoCTF{b...a}`
