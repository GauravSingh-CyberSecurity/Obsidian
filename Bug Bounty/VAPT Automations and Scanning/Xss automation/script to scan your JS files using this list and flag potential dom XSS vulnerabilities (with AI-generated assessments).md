

Chatgpt: Would you like a script to scan your JS files using this list and flag potential XSS vulnerabilities (with AI-generated assessments)?

My response: Yes


Chatgpt:

It looks like the `openai` Python package isn’t currently installed in this environment. Here's what you can do:

---

## ✅ Step-by-Step: Run This Script on Your Local Machine

### 1. **Install Required Packages**

Make sure Python is installed, then run:

```bash
pip install openai
```

---

### 2. **Save This Script (Edit Your API Key)**

```python
import os
import re
import openai

# === CONFIG ===
JS_FOLDER = "path/to/your/jsdump"  # <-- Change this to your JS folder
openai.api_key = "YOUR_OPENAI_KEY"  # <-- Replace with your API key

# === XSS Sinks and Sources ===
xss_keywords = [
    r"document\.write",
    r"document\.writeln",
    r"innerHTML",
    r"outerHTML",
    r"insertAdjacentHTML",
    r"eval\(",
    r"Function\(",
    r"setTimeout\(",
    r"setInterval\(",
    r"location\.href",
    r"location\.search",
    r"location\.hash",
    r"document\.URL",
    r"document\.referrer",
    r"window\.name",
    r"on\w+="  # onerror, onclick, etc.
]

def scan_and_analyze():
    for filename in os.listdir(JS_FOLDER):
        if filename.endswith(".js"):
            with open(os.path.join(JS_FOLDER, filename), "r", encoding="utf-8", errors="ignore") as f:
                lines = f.readlines()
                for i, line in enumerate(lines):
                    if any(re.search(k, line) for k in xss_keywords):
                        print(f"\n[+] Suspicious line in {filename}, line {i+1}:")
                        print(f"    {line.strip()}")

                        # AI Analysis
                        response = openai.ChatCompletion.create(
                            model="gpt-4",
                            messages=[
                                {"role": "system", "content": "You are a JavaScript security expert."},
                                {"role": "user", "content": f"Is this code vulnerable to XSS? Explain:\n{line.strip()}"}
                            ]
                        )
                        print("[AI Review]:", response["choices"][0]["message"]["content"])

if __name__ == "__main__":
    scan_and_analyze()
```

---

### 3. **What It Does**

- Scans `.js` files for suspicious XSS keywords.
- Sends suspicious lines to ChatGPT via OpenAI API.
- Returns GPT-powered analysis explaining if it's exploitable.

---

Would you like a **ready-to-run version as a `.zip`** or in a GitHub repo format?