```bash
# L1: domain.com (base + 2 subdomain parts)
awk -F'.' '{print $(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs1_domain.txt

# L2: a.domain.com
awk -F'.' '{if (NF>3) print $(NF-3)"."$(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs2_domain.txt

# L3
awk -F'.' '{if (NF>4) print $(NF-4)"."$(NF-3)"."$(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs3_domain.txt

# L4
awk -F'.' '{if (NF>5) print $(NF-5)"."$(NF-4)"."$(NF-3)"."$(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs4_domain.txt

# L5
awk -F'.' '{if (NF>6) print $(NF-6)"."$(NF-5)"."$(NF-4)"."$(NF-3)"."$(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs5_domain.txt

# L6+
awk -F'.' '{if (NF>7) print $(NF-7)"."$(NF-6)"."$(NF-5)"."$(NF-4)"."$(NF-3)"."$(NF-2)"."$(NF-1)"."$NF}' subs_domain.txt | sort -u > subs6_domain.txt
```

```bash
#!/bin/bash

# ──────────────────────────────────────────────
#     SUBDOMAIN LEVEL SPLITTER by Arch Load   
# ──────────────────────────────────────────────
banner() {
    clear
    echo -e "\e[34m"
    echo "   _____       _     _                        _            _         "
    echo "  / ____|     | |   | |                      | |          | |        "
    echo " | (___  _   _| |__ | | ___  ___ ___  _ __ __| | ___ _ __ | |_ ___   "
    echo "  \___ \| | | | '_ \| |/ _ \/ __/ _ \| '__/ _\` |/ _ \ '_ \| __/ _ \  "
    echo "  ____) | |_| | |_) | |  __/ (_| (_) | | | (_| |  __/ | | | || (_) | "
    echo " |_____/ \__,_|_.__/|_|\___|\___\___/|_|  \__,_|\___|_| |_|\__\___/  "
    echo "                                                                     "
    echo "                🛠 Subdomain Level Grouping Tool 🛠                 "
    echo "                     Author: Arch Load | CrookSec                   "
    echo -e "\e[0m"
}

banner

# Ask user to input the subdomain file
read -p "Enter your subdomain file (default: subs_domain.txt): " input
input=${input:-subs_domain.txt}

# Set max levels to extract
max_level=10

# Check if file exists
if [[ ! -f "$input" ]]; then
    echo -e "\e[31m[-] Input file '$input' not found!\e[0m"
    exit 1
fi

echo -e "\e[36m[*] Splitting subdomains by level from $input...\e[0m"

# Loop through levels
for (( level=1; level<=max_level; level++ )); do
    output="subs${level}_domain.txt"
    echo -e "\e[33m[+] Generating $output\e[0m"

    awk -F'.' -v L="$level" '{
        if (NF > L) {
            out = $(NF-L)
            for (i=(L-1); i>=0; i--) {
                out = out "." $(NF-i)
            }
            print out
        }
    }' "$input" | sort -u > "$output"
done

echo -e "\e[32m[✔] Done. All subdomains grouped by level!\e[0m"

```