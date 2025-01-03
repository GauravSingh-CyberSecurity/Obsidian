
here i have encrypted a P.T password wordlist using AES CBC openssl algo because the application uses this encryption algo in P.W parameter in the login request (application is staging.digicompany)

while read -r password; do
  echo -n "$password" | openssl enc -aes-256-cbc -salt -base64 -pass pass:YourPassword
done < /home/kali/SecLists/Passwords/500-worst-passwords.txt
