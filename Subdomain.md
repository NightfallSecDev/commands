```bash
subfinder -d hackerone.com
subfinder -d calculator.net -all -o subfinder.txt
```

```bash
assetfinder --subs-only example.com
```

```bash
amass enum -passive -d example.com
```

```bash
curl -s "https://crt.sh/?q=%25.example.com&output=json" | jq -r '.[].name_value' | sort -u
```

```bash
findomain -t example.com
```

```bash
amass enum -active -d example.com
```
```bash
gospider -d 0 -s "https://google.com" -c 5 -t 100 -d 5 --blacklist jpg,jpeg,gif,css,tif,tiff,png,ttf,woff,woff2,ico,pdf,svg,txt | grep -Eo '(http|https)://[^/"]+' | anew
```


