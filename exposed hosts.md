

## 🌐 1. **Shodan** – “The search engine for Internet-connected devices”

**Website**: [https://www.shodan.io](https://www.shodan.io)

### 🔎 Example Searches:
- Exposed webcams:  
  `webcamXP`
- Apache servers in India:  
  `apache country:"IN"`
- Find specific port open (e.g., RDP):  
  `port:3389`

### 🔧 CLI Example:
```bash
shodan search "nginx port:80"
shodan host 1.2.3.4
```

---

## 🌍 2. **Censys**

**Website**: [https://search.censys.io](https://search.censys.io)

### 🔎 Example Queries:
- Open Elasticsearch:  
  `services.service_name: "elasticsearch"`
- Apache servers running on port 8080:  
  `services.service_name: "http" AND services.port: 8080 AND services.http.response.body: "Apache"`

### 🔧 CLI Example:
```bash
censys search 'services.tls.certificates.leaf_data.subject.common_name: "*.google.com"'
```

---

## 🌏 3. **FOFA (China-based, very detailed)**

**Website**: [https://fofa.info](https://fofa.info)

### 🔎 Example Queries:
- IP with port 7001 open (WebLogic):  
  `port="7001"`
- Country India, using Apache:  
  `country="IN" && server="Apache"`

### 🔧 API Example (Python):
```python
https://fofa.info/api/v1/search/all?email=xxx&key=xxx&qbase64=base64_query
```

---

## 🔥 4. **Hunter How / Hunter.io** (More about email/domain recon)

**Website**:  
- [https://hunter.io](https://hunter.io) *(Email recon)*
- [https://hunterhow.com](https://hunterhow.com) *(Chinese IP/Port scanner)*

### Use Case:
- Discover emails tied to a domain  
  `hunter.io -> Search: example.com`

---

## 🌐 5. **Quake** – By Qianxin, similar to FOFA

**Website**: [https://quake.360.net/](https://quake.360.net/)

### 🔎 Example Queries:
- Find open Jenkins:  
  `service:"jenkins"`
- Exposed logins:  
  `title:"index of"`

---

## 🌐 6. **ZoomEye**

**Website**: [https://www.zoomeye.org](https://www.zoomeye.org)

### 🔎 Example Queries:
- Exposed MongoDB:  
  `app:"MongoDB"`
- Find Open RDP:  
  `port:"3389"`

---

## 🌎 7. **Netlas**

**Website**: [https://netlas.io](https://netlas.io)

### 🔎 Example Searches:
- `title:"login"`  
- `http.body:"admin"`  
- `cert.issuer.common_name:"Let's Encrypt"`

---

## 💥 8. **Criminal IP**

**Website**: [https://www.criminalip.io](https://www.criminalip.io)

### 🔎 Use Cases:
- Ransomware detection
- IP risk scoring
- Port & vulnerability scanning

---

## 🌍 9. **PublicWWW** – Source code indexer

**Website**: [https://publicwww.com](https://publicwww.com)

### 🔎 Example Searches:
- Sites using Google Analytics ID:  
  `UA-12345678`
- Specific JS library:  
  `"jquery.min.js"`

---

## ✅ Example Hunting Workflow

Let’s say you want to find **exposed Jenkins** servers on the internet:

### With **Shodan**:
```bash
shodan search "jenkins port:8080"
```

### With **Censys**:
```bash
services.service_name: "http" AND services.http.response.body: "Jenkins"
```

### With **ZoomEye**:
```bash
app:"Jenkins"
```



