# Operation Orchid
##### Tags
Medium\
Forensics\
picoCTF 2022\
disk\
Author: LT 'syreal' Jones
#### Description
> Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.  [Download compressed disk image](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)
## Solution
After downloading and extracting the Zip file we find the contained file of `disk.flag.img` which appears to be a DOS/MBR disk image.  

![Screenshot 2024-10-22 at 2 23 18 PM](https://github.com/user-attachments/assets/9db8fd8d-a671-4762-b134-3943f2c6bdb6)

Now we have to find the filesystem start with listing the partition tables:

![Screenshot 2024-10-22 at 2 23 58 PM](https://github.com/user-attachments/assets/f8dc9c2f-f173-4650-84fe-a9d0984d1780)

Partitions 0,1,2,3 are all very small, so listing out partition 4 is the likely scenario.

![Screenshot 2024-10-22 at 2 24 54 PM](https://github.com/user-attachments/assets/3744f703-5eea-4f0a-98d0-5b2bec9cf49a)

Looking in the `root` folder we find the `flag.txt` and `flag.txt.enc` files.

![Screenshot 2024-10-22 at 2 25 35 PM](https://github.com/user-attachments/assets/cef67377-7600-4cf9-995e-c27ba7c2d6b0)


Flag.txt is not readable only `flag.txt.enc` is.  This means we need to find how to open the encrypted file.

![Screenshot 2024-10-22 at 2 26 45 PM](https://github.com/user-attachments/assets/3df430c6-10f5-4e22-9e36-346c92bbadfb)

Let's search the command history and see if we can find references to the `flag.txt`.

![Screenshot 2024-10-22 at 2 28 39 PM](https://github.com/user-attachments/assets/676c667c-75df-4e35-939c-8fc2690ce3d4)

Looks like we found the openssl command and the password used in the encryption process.   This matches the `flag.txt.enc` Salted file in the root directory let's export the encrypted file to our local system then decrypt.

![Screenshot 2024-10-22 at 2 32 21 PM](https://github.com/user-attachments/assets/6c6dbd6a-3e9e-48e0-b6b4-1d6c75c85ebb)

#### Command list
```bash
 gunzip disk.flag.img.gz 
 mmls disk.flag.img 
 fls -o 411648 disk.flag.img 
 fls -o 411648 disk.flag.img 472
 strings -t d disk.flag.img | grep flag.txt
 icat disk.flag.img -o 411648 1782 > flag.txt.enc
 openssl aes256 -d -salt -in flag.txt.enc -out flag.txt -k <password>
 cat flag.txt
```

### Flag
`picoCTF{h...5}`
