# OS Cheat Sheet

## Windows 10

---

- During Windows 11 setup, on internet prompt, press Shift + F10 to pull up command prompt, then type: `oobe\BypassNRO`. Once the device restarts, the internet requirement will be removed.

### Show AP passwords

```cmd
netsh wlan show profile
netsh wlan show profile name=(name) key=clear
```

### Full TCP/IP Stack Reset

```cmd
netsh winsock reset
netsh int ip reset
ipconfig /release
ipconfig /renew
ipconfig /flushdns
```

### Git Checkout

```bash
git checkout -b development remotes/origin/development
```

### Grub / Ubuntu Bootloader From Dual Boot

If GRUB/Ubuntu bootloader is still launching after removing dual boot system from Windows:

1. Run `cmd.exe` with administrator privileges.
2. Run `diskpart`
3. Type: `list disk` then `sel disk X`, where X is the drive your boot files reside on.
4. Type `list vol` to see all partitions (volumes) on the disk (EFI volume will be formatted with FAT instead of NTFS)
5. Select the EFI volume by typing: `sel vol Y`, where Y is the `SYSTEM` volume (this is almost always the the EFI partition)
6. For convenience, assign a drive letter by typing: `assign letter=Z`, where Z is a free (unused) drive letter
7. Type `exit` to leave disk part
8. While still in the `cmd` prompt, type: `Z:`, where Z is the drive letter you just created.
9. Type `dir` to list directories on this mounted EFI partition
10. If you are in the right place, you should see a directory called `EFI`
11. Type: `cd EFI` and then `dir` to list the child directories inside `EFI`
12. Type: `rmdir /S ubuntu` to delete the Ubuntu boot directory

[Terminal/Console GUI Libraries](https://cpp.libhunt.com/libs/terminal/console/gui)

## Ubuntu 20.04+

---

### Highlight Terminal Output

``` bash
{command} | grep -E --color '{term}'
```

### Directory Traversal Shortcuts

``` bash
cd -
cd --
# Go to Home directory
cd ~
```

### Misc Analysis & Pentesting Tools

``` bash
# Tac untility - cat but backwards

searchsploit
exiftool - steg
python -c 'import pty; pty.spawn("/bin/bash")'

# Misc Utils

pdfinfo
poppler-utils
libimage-exiftool-perl
```

[Pentest Book - File Transfer](https://chryzsh.gitbooks.io/pentestbook/content/transfering_files.html)

### Disk and Image Commands

``` bash
lsblk
dd if=/dev/sda of=file.img bs=1M conv=sync status=progress
```

### Nmap Custom Scans

``` bash
# Nmap Random IP Scan

nmap -iR 25200000 -sL -n | grep "not scanned" | awk '{print $2}' | sort -n | uniq >! tp; head -25000000 tp >! 25M-IPs; rm tp

nmap -sP -PE -PP -PS21,22,23,25,80,113,31339 -PA80,113,443,10042 --source-port 53 -T4 -iL hosts

# Mask source as DNS probe

# Can use the base script identifier and the wildcard option within double quotes / run all scripts in category

nmap -p 21 --script "ftp-*" <ip_address>

Nmap -O ip -oX enum.xml && xsltproc enum.xml -o enum.html
```

### Configure a bluetooth device

```bash
hciconfig
```

### Execute Python script in Linux shell

```bash
# ./ ability in linux shell for pyton files
chmod 755 <script.py>
```

### Airmon Interface

```bash
# Start interface on channel X in airmon-ng

airmon-ng start wlan0 9
```

[Clearing Logs and Bash History](https://null-byte.wonderhowto.com/how-to/clear-logs-bash-history-hacked-linux-systems-cover-your-tracks-remain-undetected-0244768/)

### Patch GitHub Repository from Previous Repository History

```bash

# 1. Navigate to old repository and run
git format-patch -o /tmp/patches $(git rev-list --max-parents=0 HEAD)

# 2. Navigate to new repository and apply the patches
git am /tmp/patches/*.patch
```

### Log Unsuccessful Logins

```bash
cat << "EOF" > /root/last 
#!/bin/sh 
logread -e dropbear | grep 'Password auth succeeded for' | sed 's/^.* dropbear\[//' | sed 's/\]:.*//' | sort -u > /tmp/procids 
successfullogins="/tmp/procids" 
while IFS= read -r procid 
do 
user=$(logread -e "$procid" | grep 'Password auth succeeded for' | sed 's/^.*succeeded for //' | sed 's/ from.*//') 
ip=$(logread -e "$procid" | grep 'Password auth succeeded for' | sed 's/^.*from //' | sed 's/\:.*//') 
starttime=$(logread -e "$procid" | grep 'Password auth succeeded for' | sed 's/authpriv.*//' | sed 's/ from.*//') 
endtime=$(logread -e "$procid" | grep 'Exited normally' | sed 's/authpriv.*//' | sed 's/ from.*//') if [ -z "$endtime" ]; then endtime="still logged in" 
fi 
echo -e "$user\t$ip\t$starttime"- "$endtime" 
done < "$successfullogins" exit 0 
EOF 
chmod 755 /root/last
```
