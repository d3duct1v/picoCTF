# Blast from the past
##### Tags
Medium\
Forensics\
picoCTF 2024\
browser_webshell_solvable\
metadata\
Author: syreal
#### Description
> The judge for these pictures is a real fan of antiques. Can you age this photo to the specifications?Set the timestamps on this picture to `1970:01:01 00:00:00.001+00:00` with as much precision as possible for each timestamp. In this example, `+00:00` is a timezone adjustment. Any timezone is acceptable as long as the time is equivalent. As an example, this timestamp is acceptable as well: `1969:12:31 19:00:00.001-05:00`. For timestamps without a timezone adjustment, put them in GMT time (+00:00). The checker program provides the timestamp needed for each.Use this [picture](https://artifacts.picoctf.net/c_mimas/88/original.jpg).

Additional details will be available after launching your challenge instance.\
Submit your modified picture here:\
`nc -w 2 mimas.picoctf.net 51753 < original_modified.jpg`

Check your modified picture here:\
`nc mimas.picoctf.net 54276`
## Solution
Lets not modify anything and upload the picture to the score server, maybe we can get some more direction.

![Screenshot 2024-10-22 at 2 42 31 PM](https://github.com/user-attachments/assets/93d07bfb-ff66-4954-b550-b5c1a1a2c26e)

There are several Date timestamps, let's change them all.

![Screenshot 2024-10-22 at 2 43 04 PM](https://github.com/user-attachments/assets/7d6a1c51-c852-4693-9975-16911d439cf8)

Prior to modifying the file create a backup `cp original.jpg original.jpg.orig`.  Now that we can revert if we do too much damage, let's use `exiftool` to modify the metadata.

![Screenshot 2024-10-22 at 2 45 41 PM](https://github.com/user-attachments/assets/b9e7ff80-2e11-4485-b007-8ff6c4f6d56a)

Let's check the score server and see if we got everything.

![Screenshot 2024-10-22 at 2 46 31 PM](https://github.com/user-attachments/assets/d18b4ae5-6749-4d81-b6ae-110246ffcb93)

It appears we missed one, let's find the **TimeStamp** tag to modify:

![Screenshot 2024-10-22 at 2 48 04 PM](https://github.com/user-attachments/assets/aa00b212-69b6-4da9-b638-e65dcd55bb6f)

We need to modify the **Time Stamp** to the 1970 date/time in the prompt.  

![Screenshot 2024-10-22 at 2 49 14 PM](https://github.com/user-attachments/assets/c30b9a8c-f236-4c02-8218-abcade57713d)

Well.... Let's modify it another way.\
Using `hexedit` open the image in hex edit, use _tab_ to switch to ASCII then search _/_ for UTC.  Modify the hex values, not the ASCII.  to `30 30 30 30 31 00 00 00 00 00 00 00 00 00 00`.  The beginning boundary is `61 74 61` and the end boundary is `A1`.  Save the file with `Ctrl-X`.

![Screenshot 2024-10-22 at 2 53 22 PM](https://github.com/user-attachments/assets/dbba4b80-94bb-4fab-9731-5b37708b83df)

Submit the file.

![Screenshot 2024-10-22 at 2 54 52 PM](https://github.com/user-attachments/assets/0f4ad1d9-e05e-42b4-9066-3c2d7b34b7a4)

### Command List
```bash
cp original.jpg original.jpg.orig
exiftool -AllDates='1970:01:01 00:00:00.001' -CreateDate='1970:01:01 00:00:00.001' -DateTimeOriginal='1970:01:01 00:00:00.001' -ModifyDate='1970:01:01 00:00:00.001' -SubSecCreateDate='1970:01:01 00:00:00.001' -SubSecDateTimeOriginal='1970:01:01 00:00:00.001' -SubSecModifyDate='1970:01:01 00:00:00.001' original.jpg
hexedit --colors original.jpg
nc -w 2 mimas.picoctf.net 51753 < original_modified.jpg
nc mimas.picoctf.net 54276
```

### Flag
`picoCTF{7...6}`
