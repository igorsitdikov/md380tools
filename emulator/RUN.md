### Build ambe-codec docker image

```
sudo docker build --tag ambe/codec:latest .
```

### Run ambe-codec docker image

```
sudo docker run -v /home/path/computer:/path/container -it ambe/codec:latest bash
```

#### help 

```
https://github.com/travisgoodspeed/md380tools/wiki/MD380-Emulator
```

#### wav to amb

```
qemu-arm ./md380-emu -e -i data/file.wav -o data/file.wav.amb
```

#### amb to wav

```
qemu-arm ./md380-emu -d -i data/file.amb -o data/file.wav
```

#### wav to wav 

```
sox data/file.wav -t wav -r 8k - | qemu-arm ./md380-emu -e - - | qemu-arm ./md380-emu -d - - | sox -t raw -b 16 -e signed -r 8k -c 1 - -t wav -r 8k -c 1 data/out.wav
```