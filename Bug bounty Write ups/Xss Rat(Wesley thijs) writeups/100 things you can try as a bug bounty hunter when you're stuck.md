
Here's a list of 100 things you can try as a bug bounty hunter when you're stuck, focusing on various technical aspects and strategies you can use to find vulnerabilities and improve your skill set:

1. Review the target's documentation.

2. Study public bug bounty reports on platforms like HackerOne and Bugcrowd.

3. Test for common misconfigurations (e.g., open S3 buckets, exposed databases).

4. Scan for outdated software versions.

5. Use Burp Suite for in-depth web application scanning.

6. Run a port scan with Nmap or Masscan.

7. Look for CORS misconfigurations.

8. Test for SQL injection vulnerabilities using automated tools like SQLmap.

9. Experiment with different XSS payloads (e.g., DOM-based, reflected, stored).

10. Check for server misconfigurations (e.g., unnecessary services running).

11. Test API endpoints for improper authentication or authorization.

12. Look for broken access control using manual testing and fuzzing.

13. Examine cookies for insecure attributes (e.g., HttpOnly, Secure).

14. Check for open redirects.

15. Investigate SSRF (Server-Side Request Forgery) vulnerabilities.

16. Inspect HTTP headers for sensitive information leaks.

17. Look for open ports that shouldn't be accessible externally.

18. Perform fuzz testing on input fields.

19. Test for directory traversal vulnerabilities.

20. Investigate any WebSocket connections for weaknesses.

21. Analyze the server's error messages for sensitive data leaks.

22. Test for weak password policies.

23. Check for exposed configuration files.

24. Search for unused subdomains.

25. Test for path traversal vulnerabilities in file upload features.

26. Look for instances of broken cryptography or weak encryption.

27. Search for misconfigured Cloudflare settings.

28. Reverse engineer mobile apps for potential API leaks.

29. Use a proxy like Burp Suite or OWASP ZAP to intercept traffic.

30. Investigate API rate limiting and find ways to bypass it.

31. Look for reflected file download vulnerabilities.

32. Test for improper user input sanitization.

33. Explore business logic vulnerabilities (e.g., price manipulation).

34. Search for secrets in public Git repositories (e.g., API keys, private keys).

35. Review JavaScript for client-side logic flaws.

36. Check for exposed admin panels.

37. Investigate security headers such as CSP (Content Security Policy).

38. Test for blind SQL injection.

39. Investigate Cross-Site Request Forgery (CSRF) vulnerabilities.

40. Look for vulnerability in the way cookies are set (e.g., SameSite).

41. Test for insecure deserialization vulnerabilities.

42. Look for DNS misconfigurations.

43. Attempt to exploit insecure direct object references (IDOR).

44. Perform reverse engineering on JavaScript and mobile applications.

45. Check for unprotected API endpoints.

46. Examine the login mechanism for session fixation vulnerabilities.

47. Look for overexposed permissions in the API.

48. Inspect for improper redirections or forwarding.

49. Check for insecure communication channels (e.g., unencrypted HTTP).

50. Experiment with timing attacks on session management.

51. Test HTTP Request Smuggling vulnerabilities.




52. Look for Insecure Object References in file storage.

53. Check for missing input validation on upload forms.

54. Use a tool like Nikto to scan for web vulnerabilities.

55. Try exploiting insecure LDAP configurations.

56. Perform a fuzzing attack on web forms and input fields.

57. Look for broken cryptographic implementations in apps and APIs.

58. Check for sensitive data leaks in URLs (e.g., tokens, session IDs).

59. Test for excessive permissions for service accounts.

60. Look for Cross-Protocol attacks.

61. Analyze HTTP response bodies for vulnerabilities.

62. Check for improper handling of user files (e.g., unrestricted file uploads).

63. Use OWASP Amass to find subdomain enumeration.



64. Check for failures in the implementation of Two-Factor Authentication (2FA).

65. Look for unsafe HTTP methods like TRACE, DELETE, or PUT.

66. Attempt to brute force API keys or tokens.

67. Check for hard-coded credentials in mobile apps or client-side code.

68. Explore the use of Content-Type header for exploiting file upload vulnerabilities.

69. Look for instances where user data is used directly in system commands.

70. Check for unnecessary HTTP headers that reveal sensitive information.

71. Analyze API request signatures for flaws.

72. Examine different access control mechanisms for logical flaws.

73. Test the target's response to invalid or malformed inputs.

74. Research how third-party services (e.g., CDN, Google Analytics) are integrated and if they pose a security risk.

75. Perform SSL/TLS vulnerability checks (e.g., outdated ciphers, self-signed certificates).

76. Look for hardcoded debug or verbose error messages in production environments



77. Investigate URL encoding and decoding to identify issues.

78. Test for broken authentication workflows (e.g., JWT flaws).

79. Check for command injection vulnerabilities.

80. Test if the target is vulnerable to race conditions.

81. Examine stored procedures for SQL injection vulnerabilities.

82. Identify any SSRF that might interact with internal services.

83. Use a tool like Sublist3r for subdomain enumeration.

84. Look for the use of unsafe or deprecated cryptographic algorithms.

85. Analyze HTTP methods allowed on various endpoints to identify weaknesses.

86. Check for blind XXE (XML External Entity Injection) vulnerabilities.

87. Check if local files are being exposed or leaked.

88. Test for broken security mechanisms in file storage (e.g., AWS S3).

89. Test server-side cache vulnerabilities (e.g., Stale Cache Injection).

90. Review the use of third-party plugins or libraries for vulnerabilities.

91. Explore HTTP/2-based vulnerabilities and misconfigurations.

92. Search for leakages in JavaScript libraries (e.g., from CDN).

93. Analyze the security of the target’s CDN (e.g., Cloudflare, Fastly).



94. Check for improper access control in public-facing APIs.

95. Try bypassing Multi-Factor Authentication (MFA).

96. Look for weaknesses in OAuth implementations.

97. Investigate potential issues in CAPTCHA or other challenge mechanisms.

98. Check if WebRTC can be exploited for revealing internal IP addresses.

99. Perform a security audit of the target's DNS records.

100. Experiment with social engineering (e.g., phishing) as part of a responsible engagement.