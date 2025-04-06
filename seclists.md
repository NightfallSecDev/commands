

---

## 🔍 **1. Subdomain Enumeration & DNS Brute-Force**
Used for discovering subdomains and DNS records.

| Purpose | Path |
|--------|------|
| Common DNS names | `/usr/share/seclists/Discovery/DNS/namelist.txt` |
| Subdomain brute-force | `/usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt` |
| Top DNS subdomains | `/usr/share/seclists/Discovery/DNS/top-100.txt` |
| Large DNS brute-force | `/usr/share/seclists/Discovery/DNS/bitquark-subdomains-top100000.txt` |
| DNS Recon (JHaddix) | `/usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt` |
| VHost Fuzzing | `/usr/share/seclists/Discovery/DNS/vhost-top-10000.txt` |

---

## 📁 **2. Directory & Web Content Discovery**
Used for discovering hidden directories and files.

| Purpose | Path |
|--------|------|
| Common files and folders | `/usr/share/seclists/Discovery/Web-Content/common.txt` |
| Medium wordlist | `/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt` |
| Large directory list | `/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt` |
| RAFT wordlist (files) | `/usr/share/seclists/Discovery/Web-Content/raft-small-files.txt` |
| RAFT wordlist (dirs) | `/usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt` |
| Extensions brute-force | `/usr/share/seclists/Discovery/Web-Content/extensions-common.txt` |

---

## ❓ **3. URL & Parameter Discovery**
Used for fuzzing URLs, parameters, and GET/POST values.

| Purpose | Path |
|--------|------|
| Common parameter names | `/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt` |
| Basic parameters | `/usr/share/seclists/Discovery/Web-Content/params.txt` |
| API fuzzing | `/usr/share/seclists/Discovery/Web-Content/api-endpoints.txt` |

---

## 🔐 **4. Login Bruteforcing (Usernames & Passwords)**
Used for attacking login forms, SSH, FTP, etc.

| Purpose | Path |
|--------|------|
| Common passwords | `/usr/share/wordlists/rockyou.txt` |
| Top 1000 passwords | `/usr/share/seclists/Passwords/Common-Credentials/top-1000.txt` |
| Admin passwords | `/usr/share/seclists/Passwords/Leaked-Databases/rockyou.txt` |
| Top user list | `/usr/share/seclists/Usernames/top-usernames-shortlist.txt` |
| Default creds | `/usr/share/seclists/Passwords/Default-Credentials/default-passwords.csv` |

---

## ⚙️ **5. HTTP Headers, Methods, Fuzzing**
Used for advanced fuzzing of headers, methods, encoding.

| Purpose | Path |
|--------|------|
| HTTP methods | `/usr/share/seclists/Fuzzing/http-methods.txt` |
| Common headers | `/usr/share/seclists/Fuzzing/headers.txt` |
| File uploads | `/usr/share/seclists/Fuzzing/mime-content-type.txt` |
| XSS payloads | `/usr/share/seclists/Fuzzing/xss-fuzzing.txt` |

---

## 🛠️ **6. Files & Backup Discovery**
Used to discover backup files, config files, and sensitive file types.

| Purpose | Path |
|--------|------|
| Backup files | `/usr/share/seclists/Discovery/Web-Content/backup-files.txt` |
| Common config files | `/usr/share/seclists/Discovery/Web-Content/configfiles.txt` |
| Extension list | `/usr/share/seclists/Discovery/Web-Content/extensions.txt` |

---

## 🧪 **7. Payloads for Exploitation**
Used for testing vulnerabilities like SQLi, LFI, RCE, etc.

| Purpose | Path |
|--------|------|
| SQLi payloads | `/usr/share/seclists/Fuzzing/SQLi.txt` |
| LFI payloads | `/usr/share/seclists/Fuzzing/LFI/LFI-Jhaddix.txt` |
| SSTI payloads | `/usr/share/seclists/Fuzzing/SSTI/SSTI-JHADDIX.txt` |
| RCE payloads | `/usr/share/seclists/Fuzzing/RCE.txt` |

---

## 🛡️ **8. Bypass Techniques**
Used to bypass filters, firewalls, or WAFs.

| Purpose | Path |
|--------|------|
| WAF bypass | `/usr/share/seclists/Bypassing/firewalls.txt` |
| 403 bypass | `/usr/share/seclists/Bypassing/403-bypass.txt` |
| Path traversal tricks | `/usr/share/seclists/Fuzzing/path-traversal.txt` |

---

