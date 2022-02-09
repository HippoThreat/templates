## Living Off the Land
### useful programs
Useful Programs to live off the land.
```bash
which nmap aws nc ncat netcat nc.traditional wget curl ping gcc g++ make gdb base64 socat python python2 python3 python2.7 python2.6 python3.6 python3.7 perl php ruby xterm doas sudo fetch docker lxc ctr runc rkt kubectl 2>/dev/null
```
```output
```

### Compilers
Is there a compiler installed on the host?
```bash
(dpkg --list 2>/dev/null | grep "compiler" | grep -v "decompiler\|lib" 2>/dev/null || yum list installed 'gcc*' 2>/dev/null | grep gcc 2>/dev/null; which gcc g++ 2>/dev/null || locate -r "/gcc[0-9\.-]\+$" 2>/dev/null | grep -v "/doc/")
```
```output
```

### enumerate program versions
```bash
<program> -v
<program --version
dpkg -l #debian
rpm -q #centos
```

## OS information
### Version
```bash
uname -a
```
``` output
```
32 or 64 bit? 
#### Potential Kernel Exploits
Any possible exploits for the above?

## Users
### Who are you?
```bash
id
```
```output
```
Any interesting groups? 
#### Environment
```bash 
(env || set) 2>/dev/null
```
```output
```
Any interesting environment variables or any sensitive information? 
#### Path
```bash
echo $PATH
```
```output
```
Can you write to path?Is `.` in path?  

### Other Users?
```bash
cat /etc/passwd | grep -v 'nologin' | grep -v 'false'
```
```output
```

### Other Groups
```bash
cat /etc/group
```
```output
```
Is any one part of root, adm, wheel or other interesting groups? 

## S\[UG\]ID
check out GTFOBins
### SUID
```bash
find / -perm -u=s -type f 2>/dev/null
```
```output
```
#### pkexec
New exploit might be worth trying out.

### SGID
```bash
find / -perm -s=a -type f 2>/dev/null
```
```output
```

## Sudo
### Version
```bash
sudo -V
```
```output
```
Versions less than 1.28 are vulnerable to CVE
### Current User
```bash
sudo -l 
```
```output
```

## Files
### Where did you land?
```bash
pwd
```
```output
```
#### Landing Files
```bash
ls -la
```
```output
```
Any insetting files where you landed? Configs, baks, inis or the like? 

### / files
```bash
ls -la /
```
```output
```
any interesting or hidden files in the file root?

### /home files
```bash
ls -la /home
```
```output
```
Can we read or write to any user's home directories (other than ours?)

### /tmp files
```bash 
ls -la /tmp
```
```output
```
Any interesting files in /tmp?

### /var files
#### /var/backup
```bash
ls -la /var/backups
```
```output
```
#### /var/mail
If there are other users on the box.
```bash
ls -la /var/mail
```
```output
```
Can we read any of their mail?
### /etc

#### Writeable?
``` bash
find /etc -maxdepth 1 -type f -writable
```
``` output
```
#### Readable
```bash
find /etc -maxdepth 1 -type f -readable
```
```output
```
Really looking for etc/shadow as world readable
### Writable Directories
```bash
find / -executable -writable -type d 2> /dev/null
```
```output
```
anything interesting? 

## Processes
[[#enumerate program versions]] for all interesting processes

### running as root
```bash
ps -aux | grep "^root"
```
```output
```
Anything interesting as running as root? Like SQL for example...

### All processes
```bash
ps -ef
```
```output
```
Any interesting processes running by anyone else?

## Cron
Can you write to any cron jobs or paths called by cron? Particularly root level ones
### Crontab
```bash
crontab -l
```
```output
```

### /etc/cron*
```bash
ls -al /etc/cron* /etc/at*
```
```ouput
```

### cron jobs
```bash
cat /etc/cron* /etc/at* /etc/anacrontab /var/spool/cron/crontabs/root 2>/dev/null | grep -v "^#"
```
```output
```

## Services
**TO DO**

## Network
**TO DO**
### Open Ports
```bash
(netstat -punta || ss --ntpu)
```
```output
```
Any open ports that are local only? Or connections to other machines for pivoting? 