HandBrake Wrapper, a simple tool to help automate use of HandBrake CLI.

```
usage: hbw [-h] [-s] [-p] file

Wrapper for transcoding with HandBrake. HandBrakeCLI output is written to
"log" in the same directory as ghb.

positional arguments:
  file           YAML configuration file

optional arguments:
  -h, --help     show this help message and exit
  -s, --scan     Scan inputs rather than transcode. Scan result is written to
                 <path_of_input>.scan
  -p, --pretend  Print the HandBrake commands that would be run
```

Example configuration file:

```
#YAML 1.2
---
version: 0
# Destination Options
markers: true
# Video Options
encoder: "VP9"
quality: 20.0
vfr: true
encopts: "b=0"
encoder-preset: "veryfast"
# Audio Options
aencoder: "opus"
mixdown: "stereo"
ab: "128"
arate: "48"
audio: "1"
aname: "English"
# Picture Options
auto-anamorphic: true
# Filter Options
decomb: true
# Subtitle Options
all-subtitles: true

inputs:
  - input: "/path/to/file.iso"
    titles:
      - title: 3
        output: "/output/out1.mkv"
      - title: 4
        output: "/output/out2.mkv"
        grayscale: true
      - title: 6
        output: "/output/out3.mkv"
	audio: "1,2"
	aname: "English,Commentary"
  - input: "/path/to/source/dir"
    titles:
      - title: 3
        output: "/output/out4.mkv"
      - title: 5
        output: "/output/out5.mkv"
        grayscale: true
      - title: 7
        output: "/output/out6.mkv"
	audio: "1,2"
	aname: "English,Commentary"
```

Not all HandBrakeCLI options are supported, but more can be added as needed.
