# keygenme-py
Medium\
Reverse Engineering\
picoCTF 2021\
Author: syreal
#### Description
> [keygenme-trial.py](https://mercury.picoctf.net/static/0c363291c47477642c72630d68936e50/keygenme-trial.py)

## Solution
After reading such a robust description of what we will be solving, let's download the Python script.

At the top of the program, we see some global variables being declared (not according to best practices). We have several variables: `username_trial`, `key_part_static1_trial`, `key_part_static2_trial`, `key_part_dynamic1_trial`, and `key_full_template_trial`. Looking at the key parts, this is our flag. Let's find the part of the code where key_part_dynamc1_trial is being used or modified.

![Screenshot 2024-11-05 at 10 05 26 PM](https://github.com/user-attachments/assets/74db67a3-5f20-44ad-be6c-e8359657d868)


Starting at line 140, we have a function that checks the `key_full_template_trial` variable.  Each if statement checks the `username_trial` hex value against the key value.  Well, we can just create a solver script based off this check function.

![Screenshot 2024-11-05 at 10 05 42 PM](https://github.com/user-attachments/assets/e7ff6128-2653-49a5-b3fe-8f922177d8bb)


We need to use several global variables from above. Then, we can assign the hashlib of the bytes literal username string. We can then append the `key_part_dynamic1_trial` with our missing key values.  Last we just print the completed flag.
```python
import hashlib
username_trial = b"GOUGH"

key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"

hash = hashlib.sha256(username_trial).hexdigest()
key_part_dynamic1_trial = hash[4]
key_part_dynamic1_trial += hash[5]
key_part_dynamic1_trial += hash[3]
key_part_dynamic1_trial += hash[6]
key_part_dynamic1_trial += hash[2]
key_part_dynamic1_trial += hash[7]
key_part_dynamic1_trial += hash[1]
key_part_dynamic1_trial += hash[8]

key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

print(key_full_template_trial)
```

![Screenshot 2024-11-05 at 10 06 12 PM](https://github.com/user-attachments/assets/3a18f16a-df54-4fcf-9ef4-c585bf520a53)

### Flag
`picoCTF{1n_7h3_|<3y_of_xxxxxxxx}`

