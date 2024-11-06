# m00nwalk
Medium\
Forensics\
picoCTF 2019\
Author: Joon
#### Description
> Decode this [message](https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav) from the moon.

## Solution
After much searching and reading, I discovered a Video signal, SSTV, used by NASA to transmit video from the Moon back to Earth.  

**[SSTV](https://en.wikipedia.org/wiki/Slow-scan_television)**
**Slow-scan television** (**SSTV**) is a picture transmission method, used mainly by [amateur radio operators](https://en.wikipedia.org/wiki/Amateur_radio_operator "Amateur radio operator"), to transmit and receive static pictures via radio in [monochrome](https://en.wikipedia.org/wiki/Monochrome "Monochrome") or color.

Even more searching later this was discovered. Decode SSTV on Ubuntu [here](https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04) (This is what the following solution is based on).

There is a bit of setup involved in order to get this to work.
### Setup
#### Install QMake
```bash
sudo apt-get install qt5-default libopenjp2-7-dev libpulse-dev libv4l-dev libasound2-dev libgtk-3-dev libfftw3-dev
```
#### Install pavucontrol
PulseAudio
```bash
sudo apt-get install pavucontrol
```
#### Install QSSTV
This is for transmitting and receiving SSTV.
```bash
sudo apt-get install qsstv
```
#### Configure QSSTV
```bash
pactl load-module module-null-sing sink_name=virtual-cable

# Open Pulse Audio
pavucontrol
```
Confirm Null Output is available on the Output devices Tab

```
# Open QSSTV
qsstv
```
Under Options > Configuration > Sound tab set the Input and Output to **pulse -- PulseAudio Sound Server**.

Go back to the **pavucontrol** panel, set the Recording tab to **Monitor of Null Output**.
### Decoding the signal
In QSSTV, hit the play button in the Receive tab.

In a terminal, start playing the `message.wav`.
```bash
paplay -d virtual-cable message.wav
```

#### QSSTV
In the Receive window under the SSTV tab, play with the best settings for your system.  I had the following settings
- Auto Start :heavy_check_mark:
- Autosave :heavy_check_mark:
- Sensitivity: Low
- Mode: Scottie 1

As the image comes in the flag will become visable.

![Screenshot 2024-11-06 at 5 01 54 PM](https://github.com/user-attachments/assets/29a27e06-7f3d-46aa-a5da-500d7cac99bc)

### Flag
`picoCTF{b...e}`
