# Linux Cheat Sheet

---

```bash
service --status-all | grep '\[ + \]'
```

## Tools

---

## User Information

---

|          **Command**           | **Description**                                                                                                     |
| :----------------------------: | ------------------------------------------------------------------------------------------------------------------- |
|           `lslogins`           | Displays information about known users in the system, including their login statistics.                             |
|            `finger`            | Provides information about system users, including their real names, home directories, and more.                    |
|              `id`              | Displays user identity information, including user ID, group ID, and group memberships.                             |
|            `groups`            | Shows the groups a user is a member of.                                                                             |
|            `getent`            | Retrieves entries from administrative databases, such as users and groups (`getent group`, `getent passwd`).        |
|            `users`             | Displays a list of users currently logged into the system.                                                          |
| `last` or `lastb` or `lastlog` | Shows the last login sessions of users (`last`), bad login attempts (`lastb`), or the last login times (`lastlog`). |
|              `w`               | Displays information about currently logged-in users and their processes.                                           |
|             `who`              | Shows who is currently logged into the system.                                                                      |
|            `whoami`            | Displays the current user's username.                                                                               |
|           `sudo -l`            | Lists the allowed and forbidden commands for the invoking user.                                                     |

### System Profiling

---

|             **Command**              | **Description**                                                                 |
| :----------------------------------: | ------------------------------------------------------------------------------- |
|              `uname -a`              | Displays detailed information about the system, including kernel version and architecture. |
|            `hostnamectl`             | Shows or sets the system's hostname and related settings.                       |
|               `uptime`               | Displays how long the system has been running and the load average.             |
|               `lscpu`                | Provides detailed information about the CPU architecture.                       |
|               `df -h`                | Shows disk space usage in a human-readable format.                              |
|               `lsblk`                | Lists information about all available or the specified block devices.           |
|              `free -h`               | Displays memory usage in a human-readable format.                               |
|              `dpkg -l`               | Lists all installed packages on Debian-based systems.                           |
| `apt list --installed \| head -n 30` | Shows the first 30 installed packages on Debian-based systems.                  |

### Processes

---

| **Command** | **Description**                                                                                                                                                                                |
| :---------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|    `ps`     | It provides a snapshot of the current processes. This is useful for an overview of all running processes, and various options allow you to display more detailed information.      |
|    `top`    | Offers a dynamic, real-time view of running processes. It monitors system performance and resource usage, showing which processes consume the most CPU and memory.                 |
|   `htop`    | This command is similar to `top` but with an improved interface and additional features. It allows for easier process management and includes color coding for better readability. |
|  `pstree`   | It displays processes in a tree format, showing the parent-child relationships between processes. This helps us understand how processes are related and organized.                |
|   `pidof`   | It is used to find a running program's process ID (PID) by name. This is useful when you know the process's name and need its PID for further investigation or action.             |
|   `pgrep`   | This tool searches for processes based on name and other attributes. It is useful for filtering and finding specific processes.                                                        |
|   `lsof`    | This tool lists open files and the processes that opened them. This can help identify which processes use specific files, sockets, or network connections.                             |
|  `netstat`  | It provides network-related information, including active connections and listening ports. This is useful for identifying potentially malicious network activity by processes.     |
|  `strace`   | Traces system calls and signals. This is advanced but very powerful for debugging and understanding exactly what a process is doing at a low level.                                    |
|  `vmstat`   | Reports on virtual memory statistics. It's good for getting an overview of system performance, including process scheduling and resource usage.                                        |

### Networking

---

|     **Command**     | **Description**                                                                                                                                                                                              |
| :-----------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|      `netstat`      | It displays network connections, routing tables, interface statistics, masquerade connections, and multicast memberships, which are useful for getting a snapshot of the current network status. |
|        `ss`         | Similar to `netstat`, but faster and more detailed. It dumps socket statistics and shows active connections and listening ports.                                                                     |
|      `tcpdump`      | Captures and analyzes network packets in real time. You can save these packets to a file for later analysis or filter them to focus on specific types of traffic.                                    |
|       `iftop`       | It provides a real-time display of bandwidth usage on an interface. This is handy for seeing which connections are using the most bandwidth.                                                         |
|       `lsof`        | Lists open files, including network connections. It's useful for seeing which processes are connected to the network and what ports they're using.                                                   |
|     `iptables`      | It displays, sets up, and maintains IP packet filter rules, helps manage firewall rules, and monitors network traffic.                                                                                   |
|       `nmap`        | It scans networks to discover hosts and services. This is useful for identifying devices on the network and what ports they're using.                                                                |
|       `ping`        | It tests connectivity to other network devices by sending ICMP echo request packets. It's useful for checking whether a host is reachable.                                                           |
|    `traceroute`     | Traces the path packets take to reach a destination. It helps identify where network delays or issues might be occurring.                                                                                |
|        `dig`        | Queries DNS servers for information about domain names. It helps diagnose DNS-related issues.                                                                                                            |
|     `hostname`      | Displays or sets the system's hostname and associated IP address. It's useful for identifying the local system's network identity.                                                                   |
|     `ifconfig`      | Configures network interfaces. While largely replaced by `ip` commands in modern systems, it's still useful for displaying information about network interfaces.                                     |
| `ip a` (`ifconfig`) | More powerful and versatile replacement for `ifconfig`. It can be used to configure interfaces, routing, and tunnels.                                                                                    |
|        `arp`        | Displays and modifies the system's ARP (Address Resolution Protocol) table. It's useful for associating IP addresses with MAC addresses.                                                             |
|  `route` or `ip r`  | Displays or modifies the IP routing table. It helps understand how packets are routed through the network.                                                                                               |
|       `curl`        | Transfers data from or to a server using various protocols. It's useful for testing network connections and downloading files.                                                                           |
|       `wget`        | Non-interactive network downloader. It's primarily used to download files from the web and can be useful for testing download speeds and connectivity.                                               |
|      `netcat`       | Reads and writes data across network connections using TCP or UDP. It's a versatile tool for debugging and testing network connections.                                                              |
|       `whois`       | Queries the WHOIS database for domain registration information. It's useful for gathering information about domain owners.                                                                               |
|     `nslookup`      | Queries DNS servers to obtain domain name or IP address mapping. It's useful for diagnosing DNS issues.                                                                                                  |

### Miscellaneous

---

- Get a list of network adapters and IP addresses in short form:

```bash
ip -o -4 addr list | awk '{print $2, $4}'
```

- Get interface MAC addresses:

```bash
find /sys/class/net -mindepth 1 -maxdepth 1 ! -name lo -printf "%P: " -execdir cat {}/address \;
```

- Get installed tools:

```bash
apt list --installed | head
apt list | head
apt list python3 --installed
dpkg --get-selections | grep -w "install" | head
dpkg-query -l | head
```

- Get hashing algorithm used in Linux:

```bash
sudo cat /etc/shadow

# Look for hashes that begin with a $ and compare them to this list:
$1 = MD5
$2a = Blowfish
$5 = SHA-256
$6 = SHA-512
```

- Find SUID bits set:

```bash
find / -perm -u=s -type f 2>/dev/null
```

- Find stick bits set:

```bash
find / -type d -perm -1000 -exec ls -ld {} \;
```

- Remove specific items from bash history to cover tracks post-engagement:

```bash
grep -v term ~/bash_history > ~/.bash_history
```

- Detecting a virtual machine:

```bash
ls -l /dev/disk/by-id
system-detect-virt
dmidecode
```

- Example proxy connection with SSH:

```bash
ssh -D 8080 user@intranetserver -p 443
```

- Clearing bash history:

```bash
cat /dev/null > temp
touch -r .bash_history temp
mv temp .bash_history
```

- `ip a` command with color highlighting:

```bash
# In .bashrc or .zshrc file
alias ip='ip --color=auto'
```

- Unshadow to put the usernames and password hashes back into one file:

```bash
unshadow /etc/passwd /etc/shadow > /root/file
```

- Reconfigure incorrect time zones:

```bash
sudo hwclock -s
# OR
sudo hwclock --hctosys
```

- Moving files between hosts using Python:

```bash
python -m SimpleHTTPServer <port>
wget ipaddr:port/dir
```

- Add Python repository:

```bash
sudo apt install python3-virtualenv
sudo add-apt-repository ppa:deadsnakes/ppa

# If add-apt-repository command not found:
sudo apt install software-properties-common

sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.XX 1
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.YY 2

sudo update-alternatives --config python

curl -sS https://bootstrap.pypa.io/get-pip.py | sudo python
# or for specific python versions e.g., python 3.11:
curl -sS https://bootstrap.pypa.io/get-pip.py | python3.11

# Optional - May be required
sudo apt install python3.12-venv
sudo apt install python3-virtualenv
sudo apt install python3-distutils

# PYTHON 3.12
sudo add-apt-repository ppa:deadsnakes/ppa
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.12 1
sudo apt install python3.12-venv 
python3.12 -m venv env
```

- Script version of `last` command:

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

- SSH to Metasploitable2 VM:

```bash
ssh -v -oHostKeyAlgorithms=+ssh-rsa <ip> -l msfadmin
```

- Empty a file without deleting it (Truncate): 

```bash
> file.txt
```