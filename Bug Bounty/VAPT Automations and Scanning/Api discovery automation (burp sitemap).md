Finding all APIs of an application during VAPT (Vulnerability Assessment and Penetration Testing) can be automated using multiple techniques. Here’s a structured approach:


---

Automation Methods to Discover APIs in an Application During VAPT

1. Passive Discovery

Burp Suite Proxy:

Intercept and log all API calls while navigating through the application.

==Use the "Target" → "Site Map" and "HTTP History" to extract API endpoints.==

Automate using the Burp Suite API to export API requests.


Browser DevTools (F12 → Network Tab):

Capture API requests during application usage.

Use tools like Mitmproxy to automate request logging.


Spidering & Crawling:

OWASP ZAP Spider to crawl and collect API endpoints.

Wayback Machine Scraper to check for historical endpoints.




---

2. Active Discovery

Directory & API Enumeration:

Use ffuf, dirsearch, gobuster with API wordlists (e.g., SecLists/API)

ffuf -w /path/to/api-wordlist.txt -u https://target.com/FUZZ

Run tools like feroxbuster for deeper directory scanning.


Swagger & OpenAPI Discovery:

Look for swagger.json, api-docs, openapi.json

curl -X GET https://target.com/api-docs


JS File Parsing (API Leaks in Frontend JavaScript):

Extract API endpoints from JavaScript files:

grep -oE "https?://[a-zA-Z0-9./?=_-]*" *.js

Use LinkFinder:

python3 linkfinder.py -i https://target.com -o results.html




---

3. Fuzzing for Hidden Endpoints

Parameter Bruteforcing

Use ParamMiner (Burp) or wfuzz to find undocumented API parameters.

Example with wfuzz:

wfuzz -c -z file,/path/to/api-wordlist.txt --hc 404 https://target.com/api/FUZZ


GraphQL Introspection Attacks

Check for GraphQL APIs and introspection queries:

curl -X POST https://target.com/graphql -d '{"query":"{__schema{types{name}}}"}'




---

4. Automated API Recon Tools

Kiterunner (API Path Fuzzing)

kiterunner scan -w wordlists/routes-large.kite -u https://target.com

GrapQLmap (GraphQL Endpoint Enumeration)

python3 GraphQLmap.py -u https://target.com/graphql --all

Arjun (Hidden Parameter Discovery)

python3 arjun.py -u https://target.com/api/login



---

Final Workflow Automation

Automate API Discovery with Python

You can combine all these techniques into a Python script:

import requests
from bs4 import BeautifulSoup

# List of common API endpoints
api_endpoints = ["/api/v1/", "/api/v2/", "/graphql", "/swagger.json", "/openapi.json"]

target = "https://target.com"

# Check for known API endpoints
for endpoint in api_endpoints:
    url = target + endpoint
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] API Found: {url}")

# Extract API endpoints from JavaScript files
def extract_api_from_js(url):
    response = requests.get(url)
    if response.status_code == 200:
        urls = set(re.findall(r"https?://[a-zA-Z0-9./?=_-]+", response.text))
        for u in urls:
            if "api" in u:
                print(f"[+] API Found in JS: {u}")

# Find JavaScript files in the application
soup = BeautifulSoup(requests.get(target).text, "html.parser")
for script in soup.find_all("script", src=True):
    extract_api_from_js(target + script["src"])


---

Conclusion

By combining passive monitoring (Burp, DevTools, ZAP), active fuzzing (ffuf, wfuzz, kiterunner), JS file analysis, and automation scripts, you can efficiently enumerate all APIs in an application for VAPT. Would you like help in setting up automation for a specific target?

