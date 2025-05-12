#!/bin/sh

output_file="output.txt"
echo "[*] Linux Privilege Escalation Enumeration - Started" > $output_file

# Kernel & OS info
echo "\n[+] Kernel Version:" | tee -a $output_file
uname -a | tee -a $output_file

echo "\n[+] OS Info:" | tee -a $output_file
cat /etc/issue | tee -a $output_file

# Running processes
echo "\n[+] Running Processes (saved to file):" | tee -a $output_file
ps auxw > running_processes.txt
echo "Saved to running_processes.txt" | tee -a $output_file

# Network Info
echo "\n[+] Network Routes:" | tee -a $output_file
route -n | tee -a $output_file

echo "\n[+] DNS Configuration:" | tee -a $output_file
grep -v "#" /etc/resolv.conf | tee -a $output_file

echo "\n[+] ARP Table:" | tee -a $output_file
arp -a | tee -a $output_file

echo "\n[+] Current Network Connections (saved to file):" | tee -a $output_file
netstat -auntp > network_connections.txt
echo "Saved to network_connections.txt" | tee -a $output_file

# User info
echo "\n[+] Current User Permissions:" | tee -a $output_file
whoami | tee -a $output_file
find / -user $(whoami) 2>/dev/null | tee -a $output_file

echo "\n[+] All Users UID/GID Info:" | tee -a $output_file
for user in $(cut -d: -f1 /etc/passwd); do id $user; done | tee -a $output_file

echo "\n[+] Last Logged In Users:" | tee -a $output_file
last -a | tee -a $output_file

echo "\n[+] Root Accounts:" | tee -a $output_file
awk -F: '($3 == 0 && $4 == 0) {print $1}' /etc/passwd | tee -a $output_file

# Services & Configs
echo "\n[+] Service Accounts (from /etc/passwd):" | tee -a $output_file
cat /etc/passwd | tee -a $output_file

echo "\n[+] Home Directories Access:" | tee -a $output_file
ls -als /home/* 2>/dev/null | tee -a $output_file

echo "\n[+] Sudo Permissions:" | tee -a $output_file
sudo -l | tee -a $output_file

echo "\n[+] SUID Binaries:" | tee -a $output_file
find / -perm -4000 -type f 2>/dev/null | tee -a $output_file

echo "\n[+] Config Files with 'password':" | tee -a $output_file
grep -r "password" /etc/*.conf 2>/dev/null | tee -a $output_file

echo "\n[+] /etc/shadow Access Attempt:" | tee -a $output_file
cat /etc/shadow 2>/dev/null | tee -a $output_file

echo "\n[+] /root Directory Listing:" | tee -a $output_file
ls -las /root 2>/dev/null | tee -a $output_file

echo "\n[+] History Files of Users:" | tee -a $output_file
find / -name "*history*" 2>/dev/null | tee -a $output_file

echo "\n[+] Write Access to Web Directories (/var/www):" | tee -a $output_file
touch /var/www/test_write 2>/dev/null && echo "Writable!" || echo "Not writable" | tee -a $output_file

# Crons & Services
echo "\n[+] Services & Open Ports:" | tee -a $output_file
netstat -tulpn | tee -a $output_file

echo "\n[+] Readable Service Config Files:" | tee -a $output_file
find /etc/init.d/ ! -uid 0 -type f 2>/dev/null | xargs ls -la | tee -a $output_file

echo "\n[+] Cron Jobs Configuration:" | tee -a $output_file
cat /etc/crontab | tee -a $output_file
ls -als /etc/cron.* 2>/dev/null | tee -a $output_file

echo "\n[+] World-Writable Cron Jobs:" | tee -a $output_file
find /etc/cron* -type f -perm -o+w -exec ls -l {} \; 2>/dev/null | tee -a $output_file

# Installed Software
echo "\n[+] Installed Packages:" | tee -a $output_file
dpkg -l 2>/dev/null | tee -a $output_file

# Environment
echo "\n[+] Environment Variables:" | tee -a $output_file
env | tee -a $output_file

# TTY Shell Escape Examples
echo "\n[+] Shell Escape (TTY) Techniques:" | tee -a $output_file
echo 'python -c "import pty; pty.spawn(\"/bin/sh\")"' | tee -a $output_file
echo 'perl -e "exec \"/bin/sh\";"' | tee -a $output_file

echo "\n[*] Linux Privilege Escalation Enumeration - Completed!" | tee -a $output_file
