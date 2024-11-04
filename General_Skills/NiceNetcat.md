# Nice netcat...
Easy\
General Skills\
picoCTF 2021\
Author: syreal
#### Description
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 22902`, but it doesn't speak English...
## Solution
Open a terminal and copy the command.
```shell
nc mercury.picoctf.net 22902
```
The server replied with a list of numbers, copy that list to CyberChef from decimal.
```
From_Decimal('Space',false)
```
### Flag
`picoCTF{g...f}`
