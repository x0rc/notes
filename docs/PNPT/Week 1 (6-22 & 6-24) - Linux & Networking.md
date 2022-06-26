# Linux & Networking

## Linux
- The Hacker Training Path: [https://tcm-sec.com/so-you-want-to-be-a-hacker-2022-edition/](https://tcm-sec.com/so-you-want-to-be-a-hacker-2022-edition)
- Explain Shell (for Linux): [https://explainshell.com](https://explainshell.com)
- Linux for Ethical Hackers (free on YouTube): [https://youtu.be/U1w4T03B30I](https://youtu.be/U1w4T03B30I)


## Networking

- Seven Second Subnetting: [https://www.youtube.com/watch?v=ZxAwQB8TZsM](https://www.youtube.com/watch?v=ZxAwQB8TZsM)
- Subnet Guide: [https://drive.google.com/file/d/1ETKH31-E7G-7ntEOlWGZcDZWuukmeHFe/view](https://drive.google.com/file/d/1ETKH31-E7G-7ntEOlWGZcDZWuukmeHFe/view)


## Installing and updating Tools

```bash
sudo apt update && apt upgrade
```

Tip: You might want to [PimpYourKali](https://github.com/Dewalt-arch/pimpmykali)

## Ping Sweep Script

```bash
#!/bin/bash 

if [ "$1" == "" ] 
then 
echo "You forgot an IP address!" 
echo "Syntax: ./ipsweep.sh 192.168.5" 
else 
for ip in `seq 1 254`; do ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 & done
fi
```