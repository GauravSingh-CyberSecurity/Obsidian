

It's a common and highly dangerous exploit chain: Local File Inclusion (LFI) to Remote Code Execution (RCE). While LFI on its own primarily allows an attacker to read sensitive files on a server, combining it with other vulnerabilities or misconfigurations can escalate the impact to full RCE.
Here's a breakdown of how LFI can be leveraged to achieve RCE:



==Understanding Local File Inclusion (LFI)==
An LFI vulnerability occurs when a web application includes a file based on user-supplied input without proper validation. For example, a PHP script might use something like:
<?php
  $page = $_GET['page'];
  include($page . ".php");
?>

If an attacker controls the page parameter, they can manipulate the path to include arbitrary files from the server's local file system.
Example LFI exploitation:
 * Original URL: http://example.com/index.php?page=about (includes about.php)
 * LFI attempt: http://example.com/index.php?page=../../../../etc/passwd (attempts to include /etc/passwd)
If successful, the attacker can view the contents of /etc/passwd, /etc/shadow, configuration files, logs, and other sensitive data.
Common Techniques to Escalate LFI to RCE
The core idea is to find a way to write malicious code to a file on the server (even if it's not directly writable by the web application), and then use the LFI vulnerability to include and execute that file.
Here are some common methods:
 * Log Poisoning:
   * Concept: Web servers and other services (like SSH, FTP, etc.) often log user input into log files (e.g., /var/log/apache2/access.log, /var/log/apache2/error.log, /var/log/vsftpd.log). If an attacker can inject malicious code (e.g., PHP code) into these log files through some interaction (like crafting a malicious User-Agent header in an HTTP request, or failed login attempts to other services), and then include that log file using the LFI, the server will execute the injected code.
   * Steps:
     * Identify a writable log file that the web server can read.
     * Inject malicious code into the log file (e.g., <?php system($_GET['cmd']); ?>) by making a request with a crafted header (like User-Agent) or by interacting with another service that logs input.
     * Use the LFI vulnerability to include the poisoned log file: http://example.com/index.php?page=../../../../var/log/apache2/access.log
     * The server interprets the malicious code in the log file, leading to RCE. You can then execute commands via a cmd GET parameter: http://example.com/index.php?page=../../../../var/log/apache2/access.log&cmd=ls -la
 * Abusing Upload Functionality:
   * Concept: If the web application has an upload feature (for images, documents, etc.) and it's vulnerable to LFI, an attacker might be able to upload a file containing malicious code (e.g., a PHP shell in a .jpg file) and then use the LFI to include and execute this "uploaded" file.
   * Steps:
     * Find an upload form.
     * Bypass any file type or content validation to upload a malicious file (e.g., a PHP shell inside a GIF image, or a .php file disguised as .jpg).
     * Identify the upload path (sometimes guessed, sometimes revealed by LFI).
     * Use LFI to include the uploaded malicious file: http://example.com/index.php?page=../../../../path/to/uploaded_file.jpg
 * PHP Wrappers:
   * Concept: PHP has various built-in "wrappers" that can be used with file functions. Some of these can be abused with LFI to achieve RCE.
   * php://filter/ (Information Disclosure, not direct RCE but can lead to it): This wrapper allows reading the contents of local files and applying filters (like base64 encoding). While not direct RCE, it can be used to read source code or configuration files, potentially revealing credentials or other vulnerabilities that can be chained to RCE.
     * Example: http://example.com/index.php?page=php://filter/convert.base64-encode/resource=../../../../etc/passwd
   * php://input (Requires POST request and allow_url_include): If allow_url_include is enabled (which is rare in modern, secure configurations), an attacker can use php://input to include data directly from the POST request body.
     * Example (POST request with malicious PHP in body): http://example.com/index.php?page=php://input
     * POST body: <?php system($_GET['cmd']); ?>
   * data:// (Requires allow_url_include): Similar to php://input, this allows data to be included directly in the URL.
     * Example: http://example.com/index.php?page=data://text/plain,<?php%20system($_GET['cmd']);%20?>
   * zip://: This wrapper allows accessing files within a zip archive. An attacker might upload a zip file containing a malicious PHP script (perhaps disguised as an image) and then use LFI with the zip:// wrapper to execute it.
     * Example: http://example.com/index.php?page=zip://path/to/uploaded/archive.zip%23shell.php
 * Session File Exploitation:
   * Concept: PHP session files store user session data on the server, often in /var/lib/php/sessions/sess_<session_id> or /tmp/sess_<session_id>. If an attacker can inject malicious code into their session data (e.g., through a cookie or POST parameter that's stored in the session) and then use LFI to include their own session file, it can lead to RCE.
   * Steps:
     * Identify the session file location (often found in phpinfo() or by guessing common paths).
     * Inject malicious code into a session variable (e.g., by setting a cookie value or sending a POST request that the application stores in the session).
     * Use LFI to include the session file: http://example.com/index.php?page=../../../../var/lib/php/sessions/sess_<your_session_id>
General Steps for LFI to RCE Exploitation:
 * Identify LFI: Look for parameters that control file inclusion, often in URLs like ?file=, ?page=, ?template=, ?lang=, etc. Test with directory traversal payloads (../../../../etc/passwd).
 * Information Gathering: Once LFI is confirmed, try to read critical system files to gather more information (e.g., web server logs, PHP configuration (phpinfo()), application source code, /proc/self/environ to see environment variables, including potentially injectable ones). This helps in determining potential RCE vectors.
 * Choose an RCE Vector: Based on the information gathered, select the most viable technique (log poisoning, session file, upload abuse, PHP wrappers).
 * Inject and Execute: Implement the chosen technique to inject malicious code and then use the LFI to trigger its execution.
 * Gain a Shell: The goal is usually to get a reverse shell (a connection back to your attacker machine) or a bind shell (a listener on the target machine), giving you interactive command-line access.
Prevention
The key to preventing LFI and LFI-to-RCE attacks is strict input validation and sanitization.
 * Whitelist Input: Instead of blacklisting malicious characters, only allow known good, predefined values for file inclusions.
 * Avoid Dynamic Includes: If possible, avoid using user input directly in file inclusion functions.
 * Sanitize User Input: If dynamic includes are necessary, thoroughly sanitize all user-supplied input to remove path traversal sequences (../, ..\) and other malicious characters.
 * Disable Dangerous PHP Settings: Set allow_url_include = Off in php.ini.
 * Restrict File Permissions: Ensure that web server processes have the least privileges necessary and cannot write to sensitive directories or execute arbitrary files.
 * Monitor and Log: Implement robust logging and monitoring to detect unusual access patterns or attempts to include unusual files.
LFI to RCE is a classic and impactful vulnerability chain, highlighting the importance of secure coding practices and diligent security configurations.
