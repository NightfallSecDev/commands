

## 🔐 Password Cracking

### 🔸 RockYou – Leaked Password List
```
/usr/share/wordlists/rockyou.txt.gz
📌 Most used real-world leaked password list.
🔧 For brute-forcing SSH, FTP, login forms, ZIP, RAR, etc.
```

> 💡 To use:
```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

---

## 🌐 Directory & File Brute Force (Web)

### 🔸 dirb Wordlists
```
/usr/share/wordlists/dirb/common.txt
📌 Common web directories and files

/usr/share/wordlists/dirb/big.txt
📌 Larger version for deeper brute force

/usr/share/wordlists/dirb/small.txt
📌 Smaller and faster scan

/usr/share/wordlists/dirb/extensions_common.txt
📌 Common file extensions like .php, .html
```

---

## 💣 Web Fuzzing, Payloads, Admin Panel, Params

### 🔸 wfuzz Wordlists
```
/usr/share/wordlists/wfuzz/general/common.txt
📌 General parameter names

/usr/share/wordlists/wfuzz/general/admin-panels.txt
📌 Admin panels wordlist

/usr/share/wordlists/wfuzz/general/indexes.txt
📌 Directory index file names

/usr/share/wordlists/wfuzz/injections/sql.txt
📌 SQL Injection payloads

/usr/share/wordlists/wfuzz/injections/xss.txt
📌 XSS payloads

/usr/share/wordlists/wfuzz/injections/lfi.txt
📌 LFI (Local File Inclusion) payloads

/usr/share/wordlists/wfuzz/injections/rfi.txt
📌 RFI (Remote File Inclusion) payloads

/usr/share/wordlists/wfuzz/others/common_pass.txt
📌 Common passwords

/usr/share/wordlists/wfuzz/others/names.txt
📌 Common first and last names
```

---

## 🧪 Exploit & Enumeration Wordlists

### 🔸 metasploit Wordlists
```
/usr/share/wordlists/metasploit/unix_passwords.txt
📌 Common Unix passwords

/usr/share/wordlists/metasploit/http_default_pass.txt
📌 Default HTTP login passwords

/usr/share/wordlists/metasploit/postgres_default_userpass.txt
📌 PostgreSQL default user:pass
```

---

## 🗜️ Archive File Cracking

### 🔸 fcrackzip Wordlist
```
/usr/share/wordlists/fcrackzip.txt
📌 Short password list for ZIP/RAR brute-force
🔧 Used with: fcrackzip, john, hashcat
```

> Example usage:
```bash
fcrackzip -u -D -p /usr/share/wordlists/fcrackzip.txt archive.zip
```

---

## 📁 Extras (If Available)

### 🔸 fasttrack (Metasploit)
```
/usr/share/wordlists/fasttrack.txt
📌 Simple fast password list
```

### 🔸 cewl generated lists
> You can use CEWL to generate a custom wordlist:
```bash
cewl https://target.com -w target_wordlist.txt
```

