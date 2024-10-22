# Secret of the Polyglot
##### Tags
Easy\
Forensics\
picoCTF 2024\
file_format\
polyglot\
Author: syreal

#### Description
> The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/7/flag2of2-final.pdf).
## Solution
The downloaded file is a PDF, if we open the PDF we see the second half of the flag.  We can either copy it out or use the command line `pdftotext`.
`pdftotext flag2of2-final.pdf pdf_output.txt`
![Screenshot 2024-10-22 at 12 11 20 PM](https://github.com/user-attachments/assets/22eb5493-3397-49c9-9add-a292727bd85f)


Files have a weird way of working as one type when they are actually a different file type.  Let's use `file` to see if this one has a secret.  
![Screenshot 2024-10-22 at 12 15 27 PM](https://github.com/user-attachments/assets/bf5c5f74-f4f2-4dcc-8dda-2b63c87266ba)

Copy the original file to a `png` filename, then open it with the `eog` program.

![Screenshot 2024-10-22 at 12 15 38 PM](https://github.com/user-attachments/assets/6222fdb3-e1eb-48a7-8a0e-2d7c5cb0cf13)


### Commands in Order
```bash
file flag2of2-final.pdf
cp flag2of2-final.pdf flag2of2-final.png
eog flag2of2-final.png
pdftotext flag2of2-final.pdf output.txt
cat output.txt
```

### Flag
```
picoCTF{f1u...6}
```
