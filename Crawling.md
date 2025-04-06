```bash
cat sub.txt | waybackurls
```

```bash
katana -u https://tesla.com
```

```bash
katana -u https://tesla.com,https://google.com
```
```bash
katana -list url_list.txt
```

```bash
python3 paramspider.py --domain example.com
```

```bash
scrapy startproject mycrawler
cd mycrawler
scrapy genspider allurls example.com
```

```bash
import scrapy
from urllib.parse import urljoin

class AllurlsSpider(scrapy.Spider):
    name = "allurls"
    allowed_domains = ["example.com"]
    start_urls = ["https://example.com"]
    visited = set()

    def parse(self, response):
        # Normalize current URL and yield it
        url = response.url
        if url not in self.visited:
            self.visited.add(url)
            yield {"url": url}

        # Follow all internal links
        for href in response.css('a::attr(href)').getall():
            full_url = urljoin(response.url, href)
            if self.allowed_domains[0] in full_url and full_url not in self.visited:
                yield scrapy.Request(full_url, callback=self.parse)

```
