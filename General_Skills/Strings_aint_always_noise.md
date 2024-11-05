# Static ain't always noise
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
> Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/ff4e569d6b49b92d090796d4631a2577/static)? This [BASH script](https://mercury.picoctf.net/static/ff4e569d6b49b92d090796d4631a2577/ltdis.sh) might help!
## Solution
Downloading the two files, one is a 64-bit ELF binary, and the other is a script.  

Looking at the script, it takes one argument (input file) and runs `objdump` that dissembles a given file and prints the .text section of the binary.  The script then pulls the strings from the file and writes that to a separate file.

So add the executable permission to the script and run it on the `static` binary.
```bash
chmod +x ltdis.sh
./ltdis.sh static
```
Grep for the flag on the stings file.
```bash
grep "picoCTF" static.ltdis.stings.txt
```

<img width="630" alt="Screenshot 2024-11-05 at 3 18 47 PM" src="https://github.com/user-attachments/assets/180683c6-c72d-4419-b10f-adb8c98d9410">

### Flag
`picoCTF{d...e}`
