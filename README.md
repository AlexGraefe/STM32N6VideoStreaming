# STM32N6VideoStreaming

Goal of this repo is to demonstrate two parts, writing to an SD-Card and streaming the video over WiFi.
Clone this repo and open STM32N6 and WiFiChip in VSCode. Follow the instructions in their respective READMEs.

## Compilation
Compile both projects as described in the READMEs. Compile the PC-site:
Compile PC_Site:
```bash
cd PC_Site
cmake -B build
cmake --build build
```
You might need to install ffmpeg on your system.

## How to run this example
Reset both microcontrollers. Wait till the LED on the WiFi board turns white. Then, run:
```bash
./PC_Site/build/show_stream
```

Open the serial output of the STN32N6. Once it outputs "SD-Card written", you can detatch the SD Card and plug it into your PC. 
Load the data onto your PC:

```bash
dd of=dump.bin if=[path to sd e.g. /dev/sdd1] ibs=512 obs=512 count=25000
``` 

Convert it via:
```bash
ffmpeg -f h264 -framerate 30 -i dump.bin -c copy dump.mp4
```

