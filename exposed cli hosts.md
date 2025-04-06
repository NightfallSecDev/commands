

---

## 🔧 1. **Shodan CLI**
### 📦 Install:
```bash
pip install shodan
shodan init <YOUR_API_KEY>
```

### 📌 Usage:
```bash
shodan search "apache country:IN"
shodan host 1.2.3.4
shodan count "port:21 anonymous"
```

---

## 🔧 2. **Censys CLI**
### 📦 Install:
```bash
pip install censys
censys config
```

> Provide your **API ID and Secret**.

### 📌 Usage:
```bash
censys search 'services.service_name: "http" AND services.http.response.body: "Apache"'
censys view ipv4 1.2.3.4
```

---

## 🔧 3. **FOFA CLI (fofa-cli)**

### 📦 Install:
```bash
go install github.com/iam7cn/fofa-cli@latest
```

### 📌 Usage:
```bash
fofa-cli -q 'port="7001" && country="IN"' -e your@email.com -k your_api_key
```

---

## 🔧 4. **ZoomEye CLI**

### 📦 Install:
```bash
pip install zoomeye
zoomeye init
```

> Then provide your ZoomEye username & password (not API key).

### 📌 Usage:
```bash
zoomeye search app:"jenkins"
zoomeye search port:"22" + country:"IN"
```

---

## 🔧 5. **Hunter.io (emails from domain)**

Hunter.io doesn’t have an official CLI, but you can do this with `curl`:
```bash
curl "https://api.hunter.io/v2/domain-search?domain=example.com&api_key=YOUR_API_KEY"
```

---

## 🔧 6. **PublicWWW via CLI (API)**

```bash
curl "https://publicwww.com/websites/%22google-analytics.com%22/?export=csv"
```

Or, for custom scripts:
```bash
curl "https://publicwww.com/websites/%22wp-content%22/?export=csv"
```

---

## 🔧 7. **Netlas CLI**
### 📦 Install:
```bash
pip install netlas
netlas config set --api-key <your_key>
```

### 📌 Usage:
```bash
netlas search "title:login"
netlas search "cert.subject.CN:*.example.com"
```

---

## 🔧 8. **Criminal IP (API call)**
```bash
curl -X GET "https://api.criminalip.io/v1/ip/data?ip=1.2.3.4" \
     -H "x-api-key: YOUR_API_KEY"
```

---

## 🔧 9. **HunterHow (Chinese tool - similar to FOFA)**
> No official CLI but supports `curl` or browser-based enumeration.

```bash
curl "https://hunter.qianxin.com/openApi/search?api-key=xxx&search=port=7001"
```

---
## 🔧 10. **For all**

```bash
echo 'ssl:"Uber Technologies, Inc."' | uncover
```
```bash
uncover -q dorks.txt
```
```bash
echo jira | uncover -e shodan,censys,fofa,quake,hunter,zoomeye,netlas,criminalip
```
```bash
uncover -shodan 'http.component:"Atlassian Jira"' -censys 'services.software.product=`Jira`' -fofa 'app="ATLASSIAN-JIRA"' -quake 'Jira' -hunter 'Jira' -zoomeye 'app:"Atlassian JIRA"' -netlas 'jira' -criminalip 'Jira'
```

