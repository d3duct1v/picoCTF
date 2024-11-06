# vault-door-training
Easy\
Reverse Engineering\
picoCTF 2019\
Author: Mark E. Haase
#### Description
> Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: [VaultDoorTraining.java](https://jupiter.challenges.picoctf.org/static/1afdf83322ee9c0040f8e3a3c047e18b/VaultDoorTraining.java)
## Solution
Download the file; the file is a non-compiled Java code set.  Reading the description, we are looking for a password.  Luckily, there is a password check at the bottom of the code.

![Screenshot 2024-11-05 at 9 38 04 PM](https://github.com/user-attachments/assets/43475b3e-01a2-47d6-8c3c-f85ec9d5f49a)

### Flag
`picoCTF{w...3}`
