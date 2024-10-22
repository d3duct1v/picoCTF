# Verify
##### Tags
Easy\
Forensics\
picoCTF 2024\
grep\
browser_webshell_solvable\
checksum\
Author: Jeffery John
#### Description
> People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.You can download the challenge files here: [challenge.zip](https://artifacts.picoctf.net/c_rhea/12/challenge.zip)\
> Additional details will be available after launching your challenge instance.

## Solution
Downloading and expanding the Zip file results is several items:
```
checksum.txt
decrypt.sh
files/
```
The `files` directory contains roughly 300 files.  By the looks of the setup and the description, we need to find the file inside the `files` directory that matches the `checksum.txt` SHA-256 hash.  The Linux command for this is `sha256sum`.  There are 2 ways to go about this, use grep or script something up.  Here we are going to use a script, below I'll show the grep option.  
### Option 1 - Script
Let's create a shell script that finds the specific file needed to be decrypted, and matches its hash to a checksum provided in `checksum.txt`.  We'll call it `solver.sh`:
```bash
file1=`cat checksum.txt`
echo -e "[+] checksum: $file1\n"
for i in $(ls files/);
do
    fhash=$(sha256sum files/$i)
    if echo $fhash | grep $file1; then
        echo -e "\n[*] Decrypt Output"
        ./decrypt.sh files/$i
    fi
done
```

Modify the `decrypt.sh` script for the correct file path.  Change the absolute path to a relative in both places.
> [!WARNING]
> Using relative paths is an unsafe coding practice!
```bash
"/home/ctf-player/drop-in/$file_name"
# TO
"$file_name"
```

![Screenshot 2024-10-22 at 11 53 28 AM](https://github.com/user-attachments/assets/5cb28fe4-c358-459e-9491-0877703562fa)

### Option 2 - Grep
To use `grep`, cat the contents of `checksum.txt`.  Next use `sha256sum` on all the files in `files` and redirect the output to grep.
`sha256sum files/* | grep "<checksum.txt contents>"`

![Screenshot 2024-10-22 at 12 02 15 PM](https://github.com/user-attachments/assets/f14ce280-e7e0-462c-85ff-940cc8100f3e)

Then use the provided `decrypt.sh` to find the flag.

### Command List
```bash
# Option 1
chmod +x decrypt.sh
cat checksum.txt
chmod +x solver.sh
./solver.sh

# Option 2
cat checksum.txt
sha256sum files/* | grep "<checksum.txt contents>"
./decrypt.sh files/<matching file>
```

### Flag
`picoCTF{tru...0}`
