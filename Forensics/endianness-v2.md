# endianness-v2
##### Tags
Medium\
Forensics\
picoCTF 2024\
browser_webshell_solvable\
Author: Junias Bonou
#### Description
> Here's a file that was recovered from a 32-bits system that organized the bytes a weird way. We're not even sure what type of file it is.Download it [here](https://artifacts.picoctf.net/c_titan/36/challengefile) and see what you can get out of it
## Solution
Using the challenge description and the name of the challenge hints that the file is a 32-bit byte swapped file.  Let's start looking at the filetype and the magic bytes `file` and `xxd`.\

![Screenshot 2024-10-22 at 11 09 07 AM](https://github.com/user-attachments/assets/a3574b1b-6b68-4119-8468-f684f0ca8177)

`xxd challengefile | head`

![Screenshot 2024-10-22 at 11 10 48 AM](https://github.com/user-attachments/assets/174570d9-1f8a-482a-9d87-ca5daf9d33d8)


The magic bytes are all wrong, lets reverse the bytes and see what we get.  We can use hexdump and xxd to perform this task.

`hexdump -v -e '1/4 "%08x"' -e '"\n"' challengefile | xxd -r -p reversed.txt`

Let's break the hexdump command down to what it is happening.
- `hexdump`: A utility to display the contents of a file in various formats, usually in hexadecimal form.
	- `-v`: This option makes the output verbose, meaning it prevents hexdump from collapsing repeated lines. Without `-v`, identical output lines are replaced by a single asterisk `*`.
	    
	- `-e '1/4 "%08x"'`: This is a format string option (`-e` for format), and it means:
	    - `1/4`: Process 1 group of 4 bytes at a time. This treats 4 bytes (32 bits) as a single unit, which is equivalent to reading a 32-bit word.
	    - `"%08x"`: For each group of 4 bytes, output the value as an 8-character wide hexadecimal number, padded with leading zeros (`08`), and displayed in lowercase (`x`).
	      
	- `-e '"\n"'`: After each processed group of 4 bytes, output a newline character (`\n`), ensuring each 32-bit word is printed on a new line.

- `xxd`: A utility to create a hex dump from a binary file and vice versa. In this case, it is being used to reverse the process (from hex to binary).
	- `-r`: This option tells `xxd` to work in reverse mode, converting a hex dump back into a binary format.
	- `-p`: Stands for "plain" hex dump, meaning `xxd` will expect a simple string of hexadecimal characters without any extra formatting like address offsets or ASCII characters. This option is used when processing a clean hex dump such as the one output by `hexdump`.
	- `reversed.txt`: This is the name of the file where the reversed binary data will be saved.

Let's see what we have now.\
`file reversed.txt`

![Screenshot 2024-10-22 at 11 11 52 AM](https://github.com/user-attachments/assets/a2ef39cf-ec34-49bc-b24c-75d573bd6948)

Open that image!\
`eog reversed.txt`

![Screenshot 2024-10-22 at 11 12 55 AM](https://github.com/user-attachments/assets/ca42c12a-7947-4428-b274-f5c02d39b8c4)

### Command List
```bash
file challengefile
xxd challengefile | head
hexdump -v -e '1/4 "%08x"' -e '"\n"' challengefile | xxd -r -p reversed.txt
file reversed.txt
eog reversed.txt 
```

### Flag
`picoCTF{cert!f1Ed...4}`
