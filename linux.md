

### **1. Understanding the Linux File System (15 )**


- `/bin` – Essential binaries (like the kitchen tools—you need them daily!)
- `/sbin` – System binaries (reserved for root—think of it as the parental controls folder)
- `/etc` – System configuration files (the "settings" folder where all the important stuff lives)
- `/home` – User home directories (your personal playground)
- `/root` – Root user’s home directory (admin-only access—like the CEO’s office)
- `/var` – Variable data files, including logs (where Linux secretly keeps a diary of everything happening)
- `/usr` – User-installed applications (extra tools, kind of like the app store)
- `/tmp` – Temporary files (Linux’s version of a messy teenager’s room—stuff gets cleaned up eventually)

**Demo:** *"Let’s explore these directories using basic commands. Think of this as our Linux house tour!"*

```bash
ls -l /
cd /etc && ls -la
cd /home && ls -l
```

---

### **2. User Management & Permissions (20 )**



✅ **Creating and Managing Users**

```bash
adduser hacker        # Create a new user (Welcome to the club!)
passwd hacker         # Set a password for the user (Your secret handshake)
deluser hacker        # Delete a user (You're banned!)
groupadd pentesters   # Create a new group (VIP section)
usermod -aG pentesters hacker  # Add user to group (Now you’re on the guest list)
```

✅ **Switching Users and Permissions**

```bash
whoami                # Display current user (Who am I again?)
id                    # Show user and group IDs (Your membership ID)
su hacker             # Switch to user 'hacker' (VIP entry)
sudo su               # Switch to root (Now you own the club)
```

✅ **File Permissions** (Because not everyone should have access to the VIP lounge!)

```bash
ls -l file.txt        # Check file permissions
chmod 755 file.txt    # Change file permissions
chown hacker file.txt # Change file owner
chgrp pentesters file.txt # Change file group
```

✅ **SUID and Special Permissions** (The secret keys to special privileges)

```bash
chmod u+s script.sh  # Enable SUID bit (Run as the file owner)
chmod g+s folder     # Enable SGID bit (Group privileges stay!)
chmod o+t folder     # Enable Sticky bit (No one can delete your files!)
```

---

### **4. Cron Jobs for Task Automation (15 )**



✅ **Viewing and Editing Cron Jobs**

```bash
crontab -l           # List current cron jobs (What alarms do I have?)
crontab -e           # Edit cron jobs (Set new alarms)
```

✅ **Creating Scheduled Tasks**

```bash
# Run a script every day at midnight (Like a scheduled cyber heist)
0 0 * * * /home/hacker/script.sh

# Run a command every hour (A reminder to stretch your hacking muscles)
0 * * * * echo "Hello, Hacker!" >> /home/hacker/log.txt
```

✅ **Removing Cron Jobs**

```bash
crontab -r           # Remove all cron jobs (No more alarms!)
```

---

### **5. Essential Linux Commands for Hackers (30 )**

✅ **File System Navigation**

```bash
pwd                  # Print working directory (Where am I?)
ls -la               # List files including hidden ones (What secrets are here?)
cd /path             # Change directory (Time to teleport!)
find / -name file    # Find a file in the system (Where did I lose my notes?)
```

✅ **File Manipulation**

```bash
touch file.txt       # Create a file (Linux post-it note)
echo "Hello" > file.txt  # Write text to a file (Leaving messages for yourself)
cat file.txt         # View file contents (Checking your notes)
tail -n 10 file.txt  # Show last 10 lines (Reading the last chapter)
```

✅ **Process Management** (Because sometimes, Linux acts up like a stubborn teenager)

```bash
top                  # Show running processes (What’s eating my CPU?)
ps aux               # List all processes (Show me everything!)
kill -9 PID          # Kill a process (Go to sleep, stubborn app!)
```

✅ **Networking Commands** (Hackers’ favorite playground)

```bash
ifconfig / ip a      # Show IP addresses (What’s my online identity?)
ping -c 5 8.8.8.8    # Test network connectivity (Are we online?)
netstat -tulnp       # Show open ports (Who left the doors unlocked?)
```
---

### **5. System Enumeration (20 )**



#### **Common Enumeration Commands:**

- **Checking System Information:**
```bash
uname -a             # Display system information (Kernel, architecture, etc.)
cat /etc/os-release  # Get detailed OS information (What flavor of Linux are we dealing with?)
```
- **Check for Users and Groups:**
```bash
cat /etc/passwd      # List system users (Who’s living on this machine?)
cat /etc/group       # List system groups (Who belongs to which group?)
```
- **Checking for Open Ports and Network Services:**
```bash
netstat -tulnp       # List open ports and the services using them
ss -tuln             # Another tool to list open ports
```
- **Identifying Running Processes:**
```bash
ps aux               # List all processes running on the system
top                  # View real-time system processes (Your system's activity tracker)
```
- **Check for Installed Packages:**
```bash
dpkg -l              # List installed packages on Debian-based systems
rpm -qa              # List installed packages on RedHat-based systems
```



---

### **6. Installing and Removing Packages (20 )**


#### **Installing Packages:**

- **On Debian/Ubuntu-based systems:**
```bash
sudo apt update              # Update package lists
sudo apt install package-name   # Install a package (Replace 'package-name' with the actual package)
```
- **On RedHat/CentOS-based systems:**
```bash
sudo yum install package-name   # Install a package
```
- **On Fedora:**
```bash
sudo dnf install package-name   # Install a package
```

**Example:** *"To install Nmap, a popular network scanning tool, on a Debian-based system, you'd run: `sudo apt install nmap`."*

#### **Removing Packages:**

- **On Debian/Ubuntu-based systems:**
```bash
sudo apt remove package-name      # Remove a package
sudo apt purge package-name       # Remove a package along with configuration files
```
- **On RedHat/CentOS-based systems:**
```bash
sudo yum remove package-name      # Remove a package
```
- **On Fedora:**
```bash
sudo dnf remove package-name      # Remove a package
```

---
