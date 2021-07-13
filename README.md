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

## Windows

Get powershell history:
```
type C:\Users\<username>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```
