# plumbing
Medium\
General Skills\
picoCTF 2019\
Author: Alex Fulton/Danny Tunitis
#### Description
> Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.
## Solution
Using netcat `nc` to connect to the server and port we have a lot of output stating this isn't the flag etc....

Let's save the output to a file and grep for the flag.
```bash
nc jupiter.challenges.picoctf.org 7480 > plumbing.output
grep "picoCTF" plumbing.output
```

<img width="634" alt="Screenshot 2024-11-05 at 3 26 32 PM" src="https://github.com/user-attachments/assets/d6854269-d72c-4e02-b414-3df4a897ff1a">

### Flag
`picoCTF{d...4}`
