# Tab, Tab, Attack
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
> Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/3afd18a65e42b80526aa87f9766c588b/Addadshashanammu.zip)
## Solution
Download the file and expand the zip file.  This folder has several sub folders, use tab complete to either list (ls) or move (cd) to the lowest level.  Then use stings and grep to find the flag.
```bash
unzip Addadshashanammu.zip
strings .... | grep "picoCTF"
```
### Flag
`picoCTF{l...c}`
