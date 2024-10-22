# CanYouSee
##### Tags
Easy\
Forensics\
picoCTF 2024\
browser_webshell_solvable\
Author: Mubarak Mikail
#### Description
> How about some hide and seek? Download this file [here](https://artifacts.picoctf.net/c_titan/130/unknown.zip).
## Solution
After downloading and expanding the Zip file we find a file called `ukn_reality.jpg`, after checking with `file` it is in fact a JPG file.

Let's start with `exiftool`:

![Screenshot 2024-10-22 at 1 34 52 PM](https://github.com/user-attachments/assets/76e33df5-8634-40f5-82a0-cc218b7f47b0)


Well, most URL's don't look like base64, let's decode that.

`echo "<base64>" | base64 -d`

![Screenshot 2024-10-22 at 1 35 04 PM](https://github.com/user-attachments/assets/b827f4f5-5bea-4ca0-82e3-478520d8bb69)

### Commands in Order
```bash
file ukn_reality.jpg
exiftool ukn_reality.jpg
echo "<base64> | base64 -d"
```

### Flag
`picoCTF{ME7...4}`
