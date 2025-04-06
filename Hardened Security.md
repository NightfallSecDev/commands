

## 🔐 HTTP Security Headers — Deep Dive with Attack Mapping

| **Header** | **Purpose** | **If Missing or Misconfigured** | **Related Vulnerabilities & Abuse Scenarios** |
|------------|-------------|----------------------------------|-----------------------------------------------|
| `Content-Security-Policy` | Restrict what content the browser loads. | Inline scripts, external script abuse | ✅ XSS (Reflected, Stored) <br> ✅ Data Injection <br> ✅ JS-based Keyloggers |
| `X-Frame-Options: DENY / SAMEORIGIN` | Prevents embedding in iframes. | Page can be loaded inside an attacker's iframe | ✅ Clickjacking <br> ✅ UI Redress Attacks |
| `Strict-Transport-Security` (HSTS) | Force HTTPS, protect against MITM. | Browser may fall back to HTTP | ✅ SSL Stripping <br> ✅ MITM (Man-In-The-Middle) |
| `X-Content-Type-Options: nosniff` | Prevent MIME sniffing by browsers. | Browser may treat a file as a different type | ✅ MIME Sniffing <br> ✅ Stored XSS via file upload |
| `X-XSS-Protection: 1; mode=block` *(Deprecated)* | Enable browser XSS filter. | May allow reflected XSS | ✅ Reflected XSS (bypassable) |
| `Access-Control-Allow-Origin` | Controls which domains can make cross-origin requests. | Overly broad or wildcard CORS | ✅ CORS Bypass <br> ✅ Sensitive Data Theft (e.g., tokens, emails) |
| `Referrer-Policy` | Limit what referrer info is leaked in requests. | Full referrer info can leak URLs, tokens | ✅ Information Disclosure <br> ✅ Token/ID leakage |
| `Permissions-Policy` *(Feature-Policy)* | Disable sensitive APIs (camera, mic, fullscreen, etc.) | Attacker can access features like camera, mic | ✅ Privacy Violations <br> ✅ Drive-by Exploits |
| `Cache-Control: no-store` | Prevents sensitive data caching. | Sensitive data may remain in browser cache | ✅ Credential Leak <br> ✅ Session Replay via cache |
| `Set-Cookie: Secure; HttpOnly; SameSite=Strict` | Secure cookies against JS access and CSRF. | Cookies can be stolen or used cross-site | ✅ XSS (Cookie Theft) <br> ✅ CSRF Attacks |
| `Cross-Origin-Resource-Policy` | Control who can load resources from the origin. | Data may be leaked to third parties | ✅ Resource Hijack <br> ✅ Data Leakage |
| `Cross-Origin-Embedder-Policy` | Prevents speculative side-channel attacks. | Shared memory leaks can occur | ✅ Spectre-like Attacks <br> ✅ Side-channel Timing Attacks |
| `Cross-Origin-Opener-Policy` | Isolates browsing contexts. | Can allow attackers to use shared memory & manipulate windows | ✅ Tabnabbing <br> ✅ Side-Channel Attacks |
| `Expect-CT` | Helps enforce Certificate Transparency logging. | Fake certs could be used undetected | ✅ MITM via Forged Certificates |
| `Feature-Policy` (Deprecated, replaced by Permissions-Policy) | Restrict browser features per origin. | Exploitation of sensors, camera, fullscreen | ✅ Hardware Abuse <br> ✅ Drive-by Downloads |

---

## 🧪 Real-World Exploits Based on Missing Headers

| Scenario | Exploited Header | Attack |
|---------|------------------|--------|
| A user uploads an image, but attacker uploads a `.html` file instead, which browser executes | Missing `X-Content-Type-Options` | Stored XSS via file upload |
| Site uses `Access-Control-Allow-Origin: *`, exposing private API | Misconfigured CORS header | Data leakage via malicious JavaScript |
| Site allows iframe embedding | Missing `X-Frame-Options` | Clickjacking attack to trick users |
| No CSP & allows inline scripts | Missing `Content-Security-Policy` | Stored XSS via comment form |
| Site doesn’t use HSTS | Missing `Strict-Transport-Security` | SSL Downgrade Attack (e.g., via Evil Twin Wi-Fi) |

---

## 🔍 Recon Tools to Check Headers from CLI

```bash
# Curl (Basic Header Grab)
curl -I https://example.com

# Nmap (Detailed Header Script)
nmap -p 80,443 --script http-headers example.com

# Wfuzz (Header bruteforce/detection)
wfuzz -c -w headers.txt -H "FUZZ: value" https://example.com

# Nikto (Full scan including header checks)
nikto -h https://example.com
```

---

