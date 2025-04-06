```bash
curl -s "https://api.bgpview.io/asn/15169/prefixes" | jq -r '.data.ipv4_prefixes[].prefix' > ips.txt
```

```bash
import requests
import subprocess
import sys
import ipaddress
from colorama import Fore, Style, init

# Initialize Colorama for Windows compatibility
init(autoreset=True)

# Banner
def print_banner():
    banner = f"""{Fore.CYAN}
  █████╗ ███████╗███╗   ██╗    ██████╗ ███████╗ ██████╗ ███╗   ██╗
 ██╔══██╗██╔════╝████╗  ██║    ██╔══██╗██╔════╝██╔═══██╗████╗  ██║
 ███████║███████╗██╔██╗ ██║    ██████╔╝█████╗  ██║   ██║██╔██╗ ██║
 ██╔══██║╚════██║██║╚██╗██║    ██╔═══╝ ██╔══╝  ██║   ██║██║╚██╗██║
 ██║  ██║███████║██║ ╚████║    ██║     ███████╗╚██████╔╝██║ ╚████║
 ╚═╝  ╚═╝╚══════╝╚═╝  ╚═══╝    ╚═╝     ╚══════╝ ╚═════╝ ╚═╝  ╚═══╝
    {Style.RESET_ALL}"""
    print(banner)

def get_ip_ranges(asn):
    """Fetch IPv4 prefixes for a given ASN using BGPView API."""
    try:
        url = f"https://api.bgpview.io/asn/{asn}/prefixes"
        response = requests.get(url, timeout=10)
        response.raise_for_status()
        data = response.json()

        if "data" in data and "ipv4_prefixes" in data["data"]:
            return [prefix["prefix"] for prefix in data["data"]["ipv4_prefixes"]]
        else:
            print(f"{Fore.RED}[!] No IPv4 prefixes found for this ASN.")
            return []
    except requests.RequestException as e:
        print(f"{Fore.RED}[!] Error fetching ASN data: {e}")
        return []

def expand_cidr_ranges(ip_ranges):
    """Expand CIDR ranges into individual IPs."""
    ip_list = []
    for cidr in ip_ranges:
        try:
            network = ipaddress.ip_network(cidr, strict=False)
            ip_list.extend([str(ip) for ip in network.hosts()])
        except ValueError:
            print(f"{Fore.YELLOW}[!] Invalid CIDR: {cidr}")
    return ip_list

def run_httpx_scan(ip_list):
    """Run httpx to check for live hosts."""
    try:
        with open("ips.txt", "w") as f:
            f.write("\n".join(ip_list))
        
        print(f"{Fore.BLUE}[+] Running httpx to find live hosts...")
        subprocess.run(["httpx", "-silent", "-ip", "-l", "ips.txt", "-o", "live_hosts.txt"], check=True)
        print(f"{Fore.GREEN}[+] Live hosts saved in live_hosts.txt")
    except subprocess.CalledProcessError as e:
        print(f"{Fore.RED}[!] httpx scan failed: {e}")

def find_subdomains():
    """Extract subdomains using dnsx."""
    try:
        print(f"{Fore.BLUE}[+] Extracting subdomains using dnsx...")
        subprocess.run(["dnsx", "-resp-only", "-l", "live_hosts.txt", "-o", "subdomains.txt"], check=True)
        print(f"{Fore.GREEN}[+] Subdomains saved in subdomains.txt")
    except subprocess.CalledProcessError as e:
        print(f"{Fore.RED}[!] dnsx scan failed: {e}")

if __name__ == "__main__":
    print_banner()
    asn = input(f"{Fore.MAGENTA}Enter ASN (e.g., 15169 for Google): {Style.RESET_ALL}")

    if not asn.isdigit():
        print(f"{Fore.RED}[!] Invalid ASN. Please enter a numeric ASN.")
        sys.exit(1)

    print(f"{Fore.CYAN}[+] Fetching IP ranges for ASN {asn}...")
    ip_ranges = get_ip_ranges(asn)

    if not ip_ranges:
        print(f"{Fore.RED}[!] No IPs found. Exiting.")
        sys.exit(1)

    print(f"{Fore.CYAN}[+] Expanding {len(ip_ranges)} CIDR ranges into individual IPs...")
    all_ips = expand_cidr_ranges(ip_ranges)
    
    if not all_ips:
        print(f"{Fore.RED}[!] No valid IPs extracted. Exiting.")
        sys.exit(1)

    print(f"{Fore.CYAN}[+] Total IPs expanded: {len(all_ips)}")
    
    run_httpx_scan(all_ips)
    find_subdomains()

    print(f"{Fore.GREEN}[+] Recon Complete! Check 'live_hosts.txt' and 'subdomains.txt'.")

```
