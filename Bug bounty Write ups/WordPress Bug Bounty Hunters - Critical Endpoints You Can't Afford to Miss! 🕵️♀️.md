```
https://www.linkedin.com/in/mannsapariya?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app
```

WordPress Bug Bounty Hunters: Critical Endpoints You Can't Afford to Miss! 🕵️♀️

Effective reconnaissance is key in WordPress bug bounty. It's not just about scanning; it's about knowing what to look for and where.

Here's an expanded list of WordPress endpoints to scrutinize, and their common vulnerability potentials:
Core & Admin Access Points:

    /wp-admin.php & /wp-login.php: Authentication bypass, user enumeration, XSS.

    /wp-config.php: Sensitive info disclosure (backups, misconfigs).

    /wp-config-sample.php: Default file, potential info disclosure if present.

    /wp-signup.php & /wp-activate.php: User enumeration, weak CAPTCHA, open registration.

    /xmlrpc.php: SSRF, DDoS amplification, brute-force.

    /wp-admin/admin-ajax.php: Vulnerabilities in AJAX actions (e.g., CSRF, SQLi, XSS).

    /wp-admin/setup-config.php: Re-installation, info disclosure if accessible post-install.

Content & API Endpoints:

    /wp-content/uploads/: Unrestricted file uploads, XSS, directory traversal.

    /wp-content/plugins/: Directory listing, plugin version disclosure.

    /wp-content/themes/: Directory listing, theme version disclosure.

    /wp-json/ (REST API):

        /wp-json/wp/v2/users: User enumeration, info disclosure, privilege escalation.

        /wp-json/wp/v2/plugins: Installed plugin version disclosure (CVEs).

        /wp-json/wp/v2/themes: Installed theme version disclosure (CVEs).

        /wp-json/wp/v2/comments: Unauthenticated comment posting, XSS.

    /wp-comments-post.php: Comment spam, XSS via comment content.

System & Utility Endpoints:

    /wp-includes/ [directory]: Directory listing, exposed sensitive files.

    /wp-cron.php: SSRF, resource exhaustion.

    /wp-links-opml.php & /wp-links.php: Info disclosure, XSS.

    /index.php: Core entry point, often reflects parameters.

    /wp-blog-header.php: Core file, rarely directly vulnerable but part of request flow.

    /wp-mail.php: Email-related vulnerabilities if enabled.

    /wp-settings.php: Core file, misconfigurations.

    /wp-trackback.php: Trackback spam, potential SSRF.

    /readme.html: WordPress version disclosure.

    /license.txt: WordPress version disclosure.

    /wp-app.php: (If present) Mobile app integration points, potential API flaws.

Pro-Tips for High-Impact Finds:

    Fuzzing: Actively fuzz parameters (id, author, post, s, file, page) for hidden logic.

    Version Disclosure: Fingerprint WordPress, plugin, and theme versions for known CVEs.

    Auth vs. Unauth: Test all endpoints with unauthenticated users and various authenticated roles.

What other WordPress endpoints consistently yield results in your bug bounty hunts? Share your expertise below! 👇

#WordPress #BugBounty #WebSecurity #SecurityResearch #Cybersecurity #Reconnaissance #VulnerabilityResearch #Hacking