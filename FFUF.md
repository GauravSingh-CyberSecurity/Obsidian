https://www.freecodecamp.org/news/web-security-fuzz-web-applications-using-ffuf/

```
ffuf -u http://localhost:3000/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt

```

Note: Here, the “FUZZ” keyword is used as a placeholder. Ffuf will try to hit the URL by replacing the word “FUZZ” with every word in the wordlist.