```bash
gobuster dir -u https://example.com -w wordlist.txt -t 50 -x php,html,txt
```
```bash
ffuf -u https://example.com/FUZZ -w wordlist.txt -mc 200
```

```bash
ffuf -u https://example.com/FUZZ -w wordlist.txt -e .php,.html,.bak -mc 200
```

```bash
wfuzz -c -w wordlist.txt --hc 404 https://example.com/FUZZ
```
