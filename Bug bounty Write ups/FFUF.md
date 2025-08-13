
FFUF patterns that consistently surface attack surface fast:

Directories and extensions
ffuf -w raft-medium-words.txt -u https://target.com/FUZZ -e .php,.aspx,.jsp,.json,.xml -mc 200,204,301,302,307,401,403 -t 150 -ac

Parameter discovery (GET)
ffuf -w params.txt -u "https://lnkd.in/datbB7mP" -mc 200,400,401,403,500 -t 150 -ac

Parameter discovery (POST form)
ffuf -w params.txt -X POST -d "FUZZ=test" -H "Content-Type: application/x-www-form-urlencoded" -u https://lnkd.in/dFmAcARP -mc 200,400,401,403,500 -t 150 -ac

Virtual host discovery
ffuf -w subdomains.txt -H "Host: FUZZ.target.com" -u https://target.com -fs 0 -t 200 -ac

File leaks
ffuf -w leaks.txt -u https://target.com/FUZZ -mc 200 -ac
(leaks.txt: .git/.git/config,.env,.DS_Store,backup.zip,db.sql,composer.json,package.json,yarn.lock,webpack.config.js,config.php,config.js)


