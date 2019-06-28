# Scripts
I will be putting fixed, modified or created scripts here that are not necessarily part of a project.

# ssh-check-username.py
Original: https://bugfuzz.com/stuff/ssh-check-username.py
I had an issue running this script with the current Kali. The problem is with changes to paramiko. See: https://github.com/paramiko/paramiko/issues/1314

The solution is to replace instances of the text _handler_table with _client_handler_table.
I will place the fixed file on this repo.
