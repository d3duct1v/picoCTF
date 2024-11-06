# First Grep
Easy\
General Skills\
picoCTF 2019\
Author: Alex Fulton/Danny Tunitis
#### Description
> Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/495d43ee4a2b9f345a4307d053b4d88d/file)? This would be really tedious to look through manually, something tells me there is a better way.
## Solution
Download the file and use grep to find the flag.
```bash
grep "pico" file
```
### Flag
`picoCTF{g...5}`
