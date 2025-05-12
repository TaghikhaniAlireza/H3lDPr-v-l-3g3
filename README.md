# H3lDPr-v-l-3g3

# 🛠️ Linux Privilege Escalation Script

Hey —  
This is a simple bash script I wrote for enumerating common privilege escalation vectors on Linux systems. It's mainly for educational purposes, CTFs, or lab environments. The idea is to run a bunch of basic checks to help identify misconfigurations or potential security risks.

---

## 🔍 What It Checks

The script covers a wide range of system information, including:

- Kernel and OS version
- Running processes and privileges
- Network routes and active connections
- DNS and ARP data
- SUID binaries
- User and group information
- Crontab jobs and scheduled tasks
- World-writable and readable files
- Shadow file access
- Open ports and services
- Installed software packages and versions
- Environment variables
- Config files that may contain credentials
- Remote shell options (netcat, bash TCP, etc.)
- Possible ways to escape restricted shells or get TTY access

---

## 🚀 Usage

```bash
chmod +x Linux_Privilege_Escalation.sh
./Linux_Privilege_Escalation.sh
```

You can also redirect the output to a file if you'd like to save the results:

```bash
./Linux_Privilege_Escalation.sh > enum_output.txt
```

Note: Some checks may require root or sudo to give meaningful results.

---

## ⚠️ Disclaimer

**This script is intended for educational use only.**  
Please do **not** run this on any system you don’t have explicit permission to test.

---

## 💬 Contact

If you have suggestions, found bugs, or want to collaborate:

**Alireza Taghikhani**  
📧 alirezataghikhani1998@gmail.com  
GitHub: [@TaghikhaniAlireza](https://github.com/TaghikhaniAlireza)

---

Made for learning. Contributions or feedback are always welcome!
