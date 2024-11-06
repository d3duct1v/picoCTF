# m00nwalk2
Hard\
Forensics\
picoCTF 2019\
Author: Joon
#### Description
> Revisit the last transmission. We think this [transmission](https://jupiter.challenges.picoctf.org/static/599404f0bf7426a5a5c2deb538860cda/message.wav) contains a hidden message. There are also some clues [clue 1](https://jupiter.challenges.picoctf.org/static/599404f0bf7426a5a5c2deb538860cda/clue1.wav), [clue 2](https://jupiter.challenges.picoctf.org/static/599404f0bf7426a5a5c2deb538860cda/clue2.wav), [clue 3](https://jupiter.challenges.picoctf.org/static/599404f0bf7426a5a5c2deb538860cda/clue3.wav).

## Solution
Using the same message.wav file from m00nwalk, we have been provided three clue wav files. Decoding each clue points us to what we need to do.  The only file required to be done is clue1.wav.
### Decoding the signal
In QSSTV, hit the play button in the Receive tab.

In a terminal, start playing the `clue1.wav`.
```bash
paplay -d virtual-cable clue1.wav
```

#### QSSTV
In the Receive window under the SSTV tab, play with the best settings for your system.  I had the following settings:
- Auto Start :heavy_check_mark:
- Autosave :heavy_check_mark:
- Sensitivity: Low
- Mode: Auto

As the image comes in we see a password and a stegosaurus.  [Steghide](https://futureboy.us/stegano/) is a tool that can hide files in wav files.  Let's try that password on the message.wav file.
```bash
steghide extract -sf message.wav -p hidden_stegosaurus
```

We have a text file that was extracted from the sound file.
### Flag
`picoCTF{t...t}`
