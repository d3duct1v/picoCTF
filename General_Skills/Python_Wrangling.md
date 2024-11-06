# Python Wrangling
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
> Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/1b247b1631eb377d9392bfa4871b2eb1/ende.py) using [this password](https://mercury.picoctf.net/static/1b247b1631eb377d9392bfa4871b2eb1/pw.txt) to get [the flag](https://mercury.picoctf.net/static/1b247b1631eb377d9392bfa4871b2eb1/flag.txt.en)?
## Solution
Download the three files.  Reading the Python script we have to use the decrypt (-d) flag and pass the encoded flag file.  Next using the supplied password in the pw.txt we will get the flag.
```bash
cat pw.txt | python3 ende.py -d flag.txt.en
```

![Screenshot 2024-11-05 at 9 23 05 PM](https://github.com/user-attachments/assets/5e610b1e-1ad8-4090-b5d6-6fd5b371cb07)

### Flag
`picoCTF{4...4}`
