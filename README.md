# Info gathering

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

Spawn bash with python:
```
python -c 'import pty;pty.spawn("/bin/bash")'
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
[Reverse shell cheat sheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

