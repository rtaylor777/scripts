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
<pre>
./ssh-check-username.py 10.0.0.20 bob
[*] Invalid username
./ssh-check-username.py 10.0.0.20 root
[+] Valid username

You can optionally specify the port to use:
./ssh-check-username.py 10.0.0.20 --port 22 root
[+] Valid username
</pre>
<br />

# find_exploits_todo_with_port
I created this script to aid in finding exploitdb exploits that may have to do with a particular port.<br />
The searchsploit tool does not have a feature to search for exploits that have to do with a particular port.
<br />
Example:<br />
<pre>
./find_exploits_todo_with_port 445
Use caution, some lines/exploits could match that have nothing to do with the port 445

Matched line from file: windows/remote/76.c: port selection as exploit works on ports other than 135(139,445,
  Exploit: Microsoft Windows - 'RPC DCOM' Remote (Universal)
      URL: https://www.exploit-db.com/exploits/76
     Path: /usr/share/exploitdb/exploits/windows/remote/76.c
    Codes: OSVDB-11460, CVE-2003-0605
 Verified: True
File Type: C source, ASCII text

Matched line from file: windows/remote/47559.py: port 446 (iptables redirected), modify traffic, then forward to destination 445.
  Exploit: Microsoft Windows Server 2012 - 'Group Policy' Security Feature Bypass (MS15-014)
      URL: https://www.exploit-db.com/exploits/47559
     Path: /usr/share/exploitdb/exploits/windows/remote/47559.py
    Codes: CVE-2015-0009
 Verified: False
File Type: Python script, ASCII text executable, with very long lines (658)

Matched line from file: windows/remote/15266.txt: port 445/tcp open and the attacker to be able to access that port. The victim also needs to be able to access port 445/
  Exploit: Microsoft Windows - NTLM Weak Nonce (MS10-012)
      URL: https://www.exploit-db.com/exploits/15266
     Path: /usr/share/exploitdb/exploits/windows/remote/15266.txt
    Codes: CVE-2010-0231, OSVDB-62253, MS10-012
 Verified: True
File Type: Ruby script, ASCII text, with very long lines (746)
</pre>
# find_nmap_scripts_todo_with_port
Sometimes you would like to list out the nmap nfs scripts that have to to with a particular port.
<br />
Example:<br />
<pre>
./find_nmap_scripts_todo_with_port 123
ntp-info.nse:-- nmap -sU -p 123 --script ntp-info <target>
ntp-monlist.nse:<code>nmap -sU -pU:123 -Pn -n --max-retries=0 <target></code>
ntp-monlist.nse:-- nmap -sU -pU:123 -Pn -n --script=ntp-monlist <target>
</pre>
<br />

# find_nmap_scripts_todo_with_service_name
Search for a service name that is provided as an argument to the script and list out the nmap nfs scripts
that potentially match.
<br />
Example:<br />
<pre>
./find_nmap_scripts_todo_with_service_name rpcbind
nfs-ls.nse:-- 111/tcp open  rpcbind
nfs-showmount.nse:-- 111/tcp open  rpcbind
rpcinfo.nse:-- 111/tcp open  rpcbind
</pre>
<br />
