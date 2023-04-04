# Scripts
I will be putting fixed, modified or created scripts here that are not necessarily part of a project.

# ssh-check-username.py
Original: https://bugfuzz.com/stuff/ssh-check-username.py<br />
I had an issue running this script with the current Kali. The problem is with changes to paramiko. <br />
See: https://github.com/paramiko/paramiko/issues/1314

The solution is to replace instances of the text '_handler_table' with '_client_handler_table'.<br />
I will place the fixed file on this repo.<br />

The purpose of this script is to use a recent vulnerability, CVE-2018-15473, to enumerate users on a system through ssh.<br />
Usage:<br />
./ssh-check-username.py 10.0.0.20 bob<br />
[*] Invalid username<br />
./ssh-check-username.py 10.0.0.20 root<br />
[+] Valid username<br />

You can optionally specify the port to use:<br />
./ssh-check-username.py 10.0.0.20 --port 22 root<br />
[+] Valid username

# find_exploits_todo_with_port
I created this script to aid in finding exploitdb exploits that may have to do with a particular port.<br />
The searchsploit tool does not have a feature to search for exploits that have to do with a particular port.
<br />
# find_nmap_scripts_todo_with_port
Sometimes you would like to list out the nmap nfs scripts that have to to with a particular port.
<br />
# find_nmap_scripts_todo_with_service_name
Search for a service name that is provided as an argument to the script and list out the nmap nfs scripts
that potentially match.
<br />
