# JS XSS AI Scanner

This tool scans JavaScript (`.js`) files for suspicious lines that may indicate DOM-based XSS vulnerabilities and uses OpenAI's GPT-4 to evaluate their risk.

## Features
- Static scan of `.js` files for common XSS sinks/sources
- GPT-4 analysis of each suspicious line
- Easy to use, plug-and-play script

## Requirements
- Python 3.7+
- `openai` library (`pip install openai`)
- An OpenAI API key

## Usage

1. Place your `.js` files inside a folder named `jsdump`
2. Replace `YOUR_OPENAI_KEY` in the script with your actual API key
3. Run the script:

```bash
python xss_ai_scanner.py
```

## Notes
- This is a static analyzer. Dynamic payload testing (like Puppeteer) can be added for full validation.
- All API usage is subject to OpenAI's pricing and rate limits.

## License
MIT
