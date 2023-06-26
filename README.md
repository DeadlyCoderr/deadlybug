# DeadlyBug | By DeadlyCoderr

## Download:

Windows: [Download](https://cdn.discordapp.com/attachments/1109304485819469900/1122946637027880970/deadlybug.zip)

### Some features
- when running a .exe file made with msfpayload & co, the file will often be recognized by antivirus software
- AVET is an antivirus evasion tool targeting windows machines with executable files
- different kinds of input payloads can be used now: shellcode, exe and dlls
- more techniques available: shellcode/dll injection, process hollowing and more
- flexible retrieval methods for payload, decryption key, etc.
- usage as a dropper
- Chaining multiple iterations of AVET enables you to add multiple evasion layers, if necessary
- combination of techniques: download your encrypted payload via powershell, while supplying the decryption key via command line argument at execution time, and finally inject your payload into another process, choosing from multiple techniques
- basic sandbox checks
- generation of adversarial examples against static detectors based on machine learning
- execute all available build scripts with build_script_tester.py, might also be interesting for researchers for building a set of "malicious" samples using different evasion and injection techniques


### Important Note

Not all techniques will evade every AV engine. If one technique or build script does not work, please test another one.
Feel free to experiment! After all this is a toolbox - yet you should wield the hammer yourself.

## Installation

__The Installtion Instruction applies for Kali 64bit and tdm-gcc!__

You can use the setup script:
```bash
./setup.sh
```

This should automatically get you started by installing/configuring wine and installing tdm-gcc.
You'll shortly have to click through the tdm-gcc installer GUI though - standard settings should be fine.
The script will also ask if you want to install AVET's dependencies, which are needed to use some of the build scripts. The fetched dependencies will be put into separate folders next to the avet folder.


Dependencies will grab the latest releases of:
- [pe_to_shellcode](https://github.com/hasherezade/pe_to_shellcode)
- [mimikatz](https://github.com/gentilkiwi/mimikatz)
- [DKMC](https://github.com/Mr-Un1k0d3r/DKMC)


If for whatever reason you want to install wine and tdm-gcc manually:
- [How to install tdm-gcc with wine](https://govolution.wordpress.com/2017/02/04/using-tdm-gcc-with-kali-2/)

## Docker

If you are not using Kali or don't want to install Metasploit on your system, you can use the Docker Container instead.
The container encapsulates Metasploit and avet and the samples will be created in your current directory.
It is also possible to use an graphical text editor like gedit.

Building the container:
```bash
sudo docker build -t avet:v0.1 .
```
Usage:
```bash
sudo docker run -it --net=host --env="DISPLAY" --volume="$HOME/.Xauthority:/root/.Xauthority:rw" -v $(pwd):/tools/avet/output avet:v0.1 /bin/bash
```
For a better experience it is recommend to alias this.
```bash
# In your .bash_profile, .bashrc or .bash_aliases

alias avet='sudo docker run -it --net=host --env="DISPLAY" --volume="$HOME/.Xauthority:/root/.Xauthority:rw" -v $(pwd):/tools/avet/output avet /bin/bash'
```
